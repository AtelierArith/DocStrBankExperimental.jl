```
LibraryProduct(paths::Vector{String}, varname::Symbol;
               deps=LibraryProduct[],
               dlopen_flags=Symbol[])
```

`LibraryProduct`を宣言し、プレフィックス内にあるライブラリを指します。`paths`にはこのライブラリの有効なパスが含まれ、`varname`はライブラリに呼び出すために使用できるJLLパッケージ内の変数の名前です。`dlopen`に渡すフラグは、`dlopen_flags`キーワード引数を使用して`Symbols`のベクターとして指定できます。

`path`の各要素は`[dirname/]basename[.versioned-ext]`の形式を取り、`dirname`と`versioned-ext`はオプションで省略可能です。したがって、以下の3つのパスはすべて同じライブラリを見つけます：

  * `lib/libnettle.so.6`
  * `lib/libnettle`
  * `libnettle.so.6`
  * `libnettle`

非Windowsターゲットでは、`dirname`を省略すると自動的に`lib`が前に追加され、Windowsターゲットでは`bin`が前に追加されます。バージョン付き拡張子を省略すると、ライブラリの任意のバージョンを使用できるようになります（通常、ライブラリは同時に1つのバージョンしか存在しないため、問題にはなりません）。
