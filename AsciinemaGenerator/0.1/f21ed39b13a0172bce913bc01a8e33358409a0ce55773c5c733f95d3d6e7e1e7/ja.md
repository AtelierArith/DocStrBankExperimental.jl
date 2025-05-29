```
cast_file(filename::String;
        mod::Module = @__MODULE__,
        start_delay::Float64 = 0.5,
        width::Int=82,
        height::Int=43,
        randomness::Float64 = 0.0,
        output_file = nothing,

        # ステートメント設定の初期値
        delay::Float64 = 0.2,
        prompt_delay::Float64 = 0.5,
        char_delay::Float64 = 0.05,
        output_row_delay::Float64 = 0.005,
        output_delay::Float64 = 0.5,

        show_julia_version::Bool=true,
        show_pkg_status::Bool=false,
        tada::Bool=false,
    ) -> String
```

Juliaファイルを.asciinemaで再生可能な`.cast`ファイルに変換します。戻り値は`.cast`ファイルの内容としての文字列です。

### キーワード引数

以下のキーワード引数はグローバル設定用です。

  * `mod`は入力Juliaスクリプトを実行するモジュールです。
  * `output_file`は出力としての`.cast`ファイルで、デフォルト値はファイルを生成しないための`nothing`です。
  * `start_delay`は最初のステートメントを実行する前の時間遅延です。
  * `width`と`height`はターミナルの幅と高さです。
  * `randomness`は時間遅延の不確実性です。
  * `show_julia_version`がtrueの場合、Juliaのウェルカムページを表示します。
  * `show_pkg_status`がtrueの場合、最初にパッケージの状態を表示します。
  * `tada`がtrueの場合、ショーの最後に`🎉`を表示します。

以下のキーワード引数は初期ステートメントごとの設定用です。

  * `prompt_delay`は`julia>`とステートメント入力の間の時間遅延です。
  * `char_delay`は2文字を入力する間の時間遅延です。
  * `output_delay`はステートメントの入力と出力の間の時間遅延です。
  * `output_row_delay`はステートメントの出力の行間の時間遅延です。
  * `delay`はステートメントを実行した後の時間遅延です。

### 例

```jldoctest; setup=:(using AsciinemaGenerator)
julia> using AsciinemaGenerator

julia> output_file = tempname()
"/tmp/jl_g7aZCDUbC7"

julia> cast_file(joinpath("test/test_input.jl"); output_file, mod=Main);

shell> asciinema play /tmp/jl_g7aZCDUbC7
```

最後の行はクリップを再生します。詳細はこのドキュメントの`再生`セクションを参照してください。

### 入力ファイル

ステートメントごとの引数は入力Juliaソースファイルでも指定できます。例：

```julia
shell> cat test/test_input.jl
@show "Hello"

using Pkg

#: 5秒待機
#+ 5
#s delay=1.0; output_row_delay=0.3

println("haa"); Pkg.status()
```

`#s`で始まる行はパラメータ設定用で、異なる代入文は`;`で区切る必要があります。`#+`で始まる行は追加の時間遅延を挿入するためのものです。他の`#`で始まる行は通常のコメントで、これも`.cast`ファイルに表示されます！

### 再生

`asciinema`をインストールするには、[公式サイト](https://asciinema.org/docs/installation)を確認してください。また、`.cast`ファイルをウェブサイトにデプロイすることもできます。このリポジトリの`demo`ブランチにある`demo`フォルダを確認して、最小限の[Franklin](https://github.com/tlienart/Franklin.jl)静的サイトの例を参照してください。
