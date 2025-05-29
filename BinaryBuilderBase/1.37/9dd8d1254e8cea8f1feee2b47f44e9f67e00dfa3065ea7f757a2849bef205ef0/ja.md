`LibraryProduct`は、存在する必要があるだけでなく、`dlopen()`可能である必要がある特別な種類の[`Product`](@ref)です。ライブラリがインストールされるディレクトリとその名前を知っている必要があります。例えば、`"/lib/libnettle.so"`を参照する`LibraryProduct`を構築するには、「ディレクトリ」は"/lib"で、「libname」は"libnettle"になります。`LibraryProduct`は、ビルド構成に基づいてlibnameを変更するソフトウェアプロジェクトがあるため、複数のlibnameをサポートできます。

---

```
LibraryProduct(libname, varname::Symbol, dir_paths=String[];
               dont_dlopen=false, dlopen_flags=Symbol[])
```

プレフィックス内にあるライブラリを指す`LibraryProduct`を宣言します。`libname`はライブラリのベース名を指定し、`varname`はライブラリに呼び出すためにJLLパッケージ内で使用できる変数の名前です。デフォルトでは、ライブラリは`libdir`内で検索されますが、`dir_paths`引数にプレフィックス内の他のディレクトリを追加できます。`dlopen`に渡すフラグを`dlopen_flags`キーワード引数で`Symbols`のベクターとして指定できます。ライブラリがJLLパッケージによって自動的にdlopenされるべきでない場合は、`dont_dlopen=true`に設定します。

例えば、`libname`が`libnettle`の場合、次のパスで満たされます：

  * LinuxおよびFreeBSDでは`lib/libnettle.so`または`lib/libnettle.so.6`；
  * macOSでは`lib/libnettle.6.dylib`；
  * Windowsでは`lib/libnettle-6.dll`。

検索パターンに一致するライブラリは、`dlopen()`可能でない場合は拒否されます。

`libname`にどの値を使用すればよいかわからない場合は、`Base.BinaryPlatforms.parse_dl_name_version`を使用できます：

```
julia> using Base.BinaryPlatforms

julia> parse_dl_name_version("sfml-audio-2.dll", "windows")[1]
"sfml-audio"
```

ライブラリが異なるオペレーティングシステムで異なるベース名を持つ場合（例：LinuxおよびFreeBSDでは`libz.so`、macOSでは`libz.dylib`、Windowsでは`zlib.dll`）、`libname`は異なる代替の`String`のベクターでも構いません：

```
LibraryProduct(["libz", "zlib"], :libz)
```
