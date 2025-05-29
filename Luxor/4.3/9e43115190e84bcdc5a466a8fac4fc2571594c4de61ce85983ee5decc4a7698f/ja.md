```
preview()
```

ノートブック（例：Jupyter/IJulia）で作業している場合は、ノートブックにPNGまたはSVGファイルを表示します。

VS-Codeで作業している場合は、PlotsペインにPNGまたはSVGファイルを表示します。

:typeの描画は、`finish()`を呼び出す前に`image_as_matrix()`で行列に変換する必要があります。

それ以外の場合：

  * macOSでは、デフォルトのアプリケーションでファイルを開きます。PNGとPDFの場合はおそらくPreview.app、SVGの場合はSafariです。
  * Unixでは、`xdg-open`でファイルを開きます。
  * Windowsでは、`COMSPEC`を参照してください。

描画を返します。
