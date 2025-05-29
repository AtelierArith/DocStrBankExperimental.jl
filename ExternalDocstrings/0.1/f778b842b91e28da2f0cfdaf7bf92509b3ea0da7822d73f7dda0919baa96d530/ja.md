```
ExternalDocstrings
```

ExternalDocstrings.jlは、マークダウンファイルでドキュメンテーション文字列を書くためのヘルパーです。

# 使用法

`src/docs/`にマークダウンファイルを作成します（`src/MyPackage.jl`がメインのパッケージソースファイルです）。`MyPackage`名前空間の中に次の行を入れてください：

```julia
ExternalDocstrings.@define_docstrings
```

これは、`src/docs/$name.md`のマークダウンコンテンツを使用して、名前`MyPackage.$name`のためのドキュメンテーション文字列を定義します。

# 拡張ヘルプ

## マークダウン変換

標準のマークダウン（およびCommonMark）を使用しながら、Juliaのドキュメンテーション文字列のための特別な構文をサポートするために、ExternalDocstrings.jlはいくつかの変換を行います：

(1) コードフェンスの表記

```julia
    # ...
    ```

は次のように変換されます：

    ```jldoctest LABEL
    # ...
    ```

ここで`LABEL`はマークダウンファイルに固有のラベルです（つまり、1つのマークダウンファイル内のすべてのコードブロックは同じセッションで実行されます）。

(2) 非REPLコードブロックのためのドクトテストを助けるために、

    nothing  # hide
    # output

は、REPLセッションのように見えず、すでに`# output`を持っていない場合、コードブロックの最後に挿入されます。

(3) `<kbd>KEY</kbd>`は`_KEY_`に置き換えられます。

## ヒント

### ドクトテストを無効にする

ドクトテストなしで構文ハイライトを有効にするには、次のようにわずかに異なるコードフェンスの表記を使用します：

    ```JULIA
    this_is_not_doctested() = nothing
    ```

### ベンダリング

ExternalDocstrings.jlは、ベンダリングを助けるために単一ソースパッケージとして書かれています。例えば、次のように簡単にインストールできます：

```

bash wget https://raw.githubusercontent.com/tkf/ExternalDocstrings.jl/main/src/ExternalDocstrings.jl -O src/ExternalDocstrings.jl ```
