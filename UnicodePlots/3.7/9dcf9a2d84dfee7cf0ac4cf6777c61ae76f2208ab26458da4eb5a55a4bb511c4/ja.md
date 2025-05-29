```
boxplot(data; kw...)
boxplot!(p, args...; kw...)
```

# 説明

ボックスプロットを描画します。

最初の引数はプロットするデータを指定します。これはベクトルのベクトルであり、各内側のベクトルはデータ系列を表します。異なる長さの系列を許可するために、行列の代わりにベクトルのベクトルを使用します。オプションで、系列の数と同じ長さのテキストのリストを提供することができます。

また、辞書を使用してボックスプロットを指定することもできます。その場合、数値でなければならない値がデータ系列として使用され、文字列でなければならないキーがラベルとして使用されます。

# 使用法

```
boxplot([text], data; border = :corners, color = :green, title = "", xlabel = "", ylabel = "", xscale = :identity, yscale = :identity, width = 40, compact = false, blend = true, xlim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, yflip = false, xflip = false, name = "")
boxplot(dict; kw...)
```

# 引数

  * **`text`** : ボックスのラベル/キャプション（オプション）。
  * **`data`** : ベクトルのベクトルで、各内側のベクトルはデータ系列を表します（異なる長さの系列を許可するためにベクトルのベクトルを選択します）。
  * **`dict`** : キーが `text` として使用され、値が `data` として使用される辞書。
  * **`color::Symbol = :auto`** : 色の `Vector`、またはスカラー - （`:green`, `:blue`, `:red`, `:yellow`, `:cyan`, `:magenta`, `:white`, `:normal`, `:auto`）から選択、または `[0-255]` の整数を使用するか、`RGB` コンポーネントとして `3` つの整数を提供します。
  * **`title::String = ""`** : プロットの上部に表示されるテキスト。
  * **`name::String = ""`** : 右側に表示される現在の描画注釈。
  * **`xlabel::String = ""`** : プロットの `x` 軸に表示されるテキスト。
  * **`ylabel::String = ""`** : プロットの `y` 軸に表示されるテキスト。
  * **`xscale::Symbol = :identity`** : `x` 軸のスケール（`:identity`, `:ln`, `:log2`, `:log10`）、またはスケール関数（例：`x -> log10(x)`）。
  * **`labels::Bool = true`** : プロットラベルを表示。
  * **`border::Symbol = :solid`** : プロットの境界ボックススタイル（`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`margin::Int = 3`** : プロット全体の左側の空白文字の数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`width::Int = 40`** : キャンバスの行ごとの文字数、または `:auto`。
  * **`xlim::Tuple = (0, 0)`** : `x` 軸のプロット範囲（`(0, 0)` は自動を意味します）。
  * **`xflip::Bool = false`** : `true` に設定すると `x` 軸を反転します。
  * **`yflip::Bool = false`** : `true` に設定すると `y` 軸を反転します。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に `Unicode` シンボルを使用します：例 `10²⸱¹` の代わりに `10^2.1`。
  * **`blend::Bool = true`** : 基盤のキャンバス上で色をブレンドします。

# 著者

  * Matthew Lake (github.com/mgtlake)

# 例

```julia-repl
julia> boxplot([1, 2, 3, 7]; title = "Test")
                       Test                    
    ┌                                        ┐ 
     ╷   ┌────┬─────────┐                   ╷  
     ├───┤    │         ├───────────────────┤  
     ╵   └────┴─────────┘                   ╵  
    └                                        ┘ 
     1                  4                   7  
```

# 参照

[`Plot`](@ref), [`histogram`](@ref), [`BoxplotGraphics`](@ref)
