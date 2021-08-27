# How-to-download-file-using-Custom-PHP

``` HTML
<a href="download.php?file=<?php echo urlencode($link); ?>">Download File</a>

```PHP
// download.php code

<?php
if(isset($_REQUEST["file"]))
{
    $file = urldecode($_REQUEST["file"]); // Decode URL-encoded string

    header('Content-Description: File Transfer');
    header('Content-Type: application/octet-stream');
    header('Content-Disposition: attachment; filename="'.basename($file).'"');
    header('Expires: 0');
    header('Cache-Control: must-revalidate');
    header('Pragma: public');
    header('Content-Length: ' . filesize($file));
    flush(); // Flush system output buffer
    readfile($file);
    die();
}
?>

