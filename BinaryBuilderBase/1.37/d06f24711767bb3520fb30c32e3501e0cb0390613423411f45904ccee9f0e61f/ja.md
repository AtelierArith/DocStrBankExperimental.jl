`ExecutableProduct`は、実行可能ファイルを表す[`Product`](@ref)です。

すべてのプラットフォームで、ExecutableProductはファイルの存在を確認します。非Windowsプラットフォームでは、実行可能ビットが設定されているかどうかを確認します。Windowsプラットフォームでは、ファイルが".exe"で終わるかどうかを確認し、存在しない場合は自動的に追加します。

---

```
ExecutableProduct(binname, varname::Symbol, dir_path="bin")
```

プレフィックス内にある実行可能ファイルを指す`ExecutableProduct`を宣言します。`binname`は実行可能ファイルのベース名を指定し、`varname`はライブラリに呼び出すために使用できるJLLパッケージ内の変数の名前です。デフォルトでは、ライブラリは`bindir`内で検索されますが、`dir_path`引数を使用してプレフィックス内の別のディレクトリを指定することもできます。
