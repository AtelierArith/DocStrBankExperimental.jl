```
getroot(p::Path, root = p.path)
```

`Path`オブジェクト`p`のパスを、まるで`root`フォルダにあるかのように返します。`p`がフォルダに対応する場合は`root`を返します。`p`がファイル`filename`に対応する場合は`joinpath(root, filename)`を返します。

!!! warning
    `getroot`の結果は必ずしも存在するパスではありません。この関数は主に、ファイルシステムとやり取りすることなく`p`に関する情報（例えば、その拡張子）を取得するために便利です。

