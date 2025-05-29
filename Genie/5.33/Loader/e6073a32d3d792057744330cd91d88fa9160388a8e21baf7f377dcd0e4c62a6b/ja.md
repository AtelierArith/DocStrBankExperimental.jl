```
@using(package_path)
```

モジュールの読み込みを簡素化するためのマクロで、事前コンパイルを活用します。Mainから呼び出されると、一時的にLOAD_PATHにパスを追加し、`using`を介してモジュールを読み込みます。別のモジュールから呼び出されると、モジュールファイルをインクルードし、`using .MyModule`を使用します。

`package_path`は以下のようにいくつかの方法で使用できます。

  * 同名のモジュールファイルを含むディレクトリへのパスとして   例: '@using models/MyApp' は 'models/MyApp/MyApp.jl' を読み込みます
  * モジュールへのパス（拡張子 '.jl' なし）として   例: '@using models/MyApp' は 'models/MyApp.jl' を読み込みます
  * 'src'ディレクトリとその中のモジュールファイルを含むパッケージディレクトリへのパスとして   例: '@using models/MyApp' は 'models/MyApp/src/MyApp.jl' を読み込みます

### 例

```julia
@using models/MyApp

@using StippleDemos/Vue3/Calendars
```

または明示的に

```julia
@using StippleDemos/Vue3/Calendars/Calendars
```

注意: コロン (`':'`) やスペース (`' '`) のような特殊文字を含むディレクトリは、二重引用符でエスケープする必要があります。

```julia
@using "C:/Program Files/Julia/models/Calendars"

# または
@using "C:/Program Files"/Julia/models/Calendars
```

注意: 事前コンパイルのため、マクロに変数を供給することはできません。呼び出しは明示的なパスを供給する必要があります。
