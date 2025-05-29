```julia
ishidden(f::AbstractString)
```

ファイルまたはディレクトリが隠れているかどうかを確認します。

Unix系システムでは、ファイルまたはディレクトリは、フルストップ/ピリオド（`U+002e`）で始まる場合に隠れていると見なされます。Windowsシステムでは、この関数はファイル属性を解析して、指定されたファイルまたはディレクトリが隠れているかどうかを判断します。

!!! note
    ディレクトリ参照（つまり、`.`または`..`）は常に隠れています。基になるパスが隠れているかどうかを確認するには、その`realpath`で`ishidden`を実行する必要があります。


!!! note
    Unix系システムでは、ファイルがフルストップで始まるかどうかを正しく判断するために、まずパスをその実際のパスに展開する必要があります。


!!! note
    BSDから派生したオペレーティングシステム（つまり、*BSD、macOS）では、この関数は`stat`の`st_flags`フィールドもチェックして、`UF_HIDDEN`フラグが設定されているかどうかを確認します。


!!! note
    macOSでは、[パッケージ](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/DocumentPackages/DocumentPackages.html)または[バンドル](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/AboutBundles/AboutBundles.html)内のファイルまたはディレクトリは、隠れていると見なされます。

