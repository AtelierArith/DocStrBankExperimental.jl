```
barplot(text, heights; kw...)
barplot!(p, args...; kw...)
```

# 説明

水平バー プロットを描画します。最初のパラメータ（`text`）はバーの名前を示し、2 番目のパラメータ（`heights`）はその値として使用されます。これは、2 つのベクトルが同じ長さである必要があることを意味します。あるいは、辞書 `dict` を使用してバー プロットを指定することもできます。その場合、キーは名前として使用され、値は数値でなければならず、バーの高さとして使用されます。

# 使用法

```
barplot(text, heights; border = :barplot, color = :green, maximum = nothing, title = "", xlabel = "", ylabel = "", xscale = :identity, width = 40, compact = false, blend = true, margin = 3, padding = 1, labels = true, unicode_exponent = true, yflip = false, xflip = false, symbols = ['■'], name = "")
barplot(dict; kw...)
```

# 引数

  * **`text`** : バーのラベル / キャプション。
  * **`heights`** : バーの値 / 高さ。
  * **`dict`** : キーが `text` として使用され、値が `heights` として使用される辞書。
  * **`xscale::Symbol = :identity`** : プロット前にバーの長さを変換するための `Function` または `Symbol`：これは、個々のバーのキャプションに影響を与えずに `x` 軸を効果的にスケーリングします（対数スケールの場合は `xscale = :log10` を使用）。
  * **`color::Symbol = :auto`** : 色の `Vector` またはスカラー - （`:green`, `:blue`, `:red`, `:yellow`, `:cyan`, `:magenta`, `:white`, `:normal`, `:auto`）から選択するか、`[0-255]` の整数を使用するか、`RGB` コンポーネントとして `3` つの整数を提供します。
  * **`maximum`** : オプションの最大高さ。
  * **`symbols::Array = ['■']`** : バーを描画するために使用される文字のコレクション。
  * **`title::String = ""`** : プロットの上部に表示されるテキスト。
  * **`name::String = ""`** : 右側に表示される現在の描画注釈。
  * **`xlabel::String = ""`** : プロットの `x` 軸に表示されるテキスト。
  * **`ylabel::String = ""`** : プロットの `y` 軸に表示されるテキスト。
  * **`labels::Bool = true`** : プロットラベルを表示します。
  * **`border::Symbol = :solid`** : プロットの境界ボックススタイル（`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`margin::Int = 3`** : プロット全体の左側の空の文字の数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`width::Int = 40`** : キャンバスの行ごとの文字数、または `:auto`。
  * **`xflip::Bool = false`** : `true` に設定すると `x` 軸が反転します。
  * **`yflip::Bool = false`** : `true` に設定すると `y` 軸が反転します。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に `Unicode` シンボルを使用します：例 `10²⸱¹` の代わりに `10^2.1`。
  * **`blend::Bool = true`** : 基盤となるキャンバスで色をブレンドします。

# 著者

  * Christof Stocker (github.com/Evizero)

# 例

```julia-repl
julia> barplot(["Paris", "New York", "Madrid"],
               [2.244, 8.406, 3.165],
               xlabel = "population [in mil]")
            ┌                                        ┐ 
      Paris ┤■■■■■■■■■ 2.244                           
   New York ┤■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■ 8.406   
     Madrid ┤■■■■■■■■■■■■ 3.165                        
            └                                        ┘ 
                        population [in mil]            
```

# 参照

[`Plot`](@ref), [`histogram`](@ref), [`BarplotGraphics`](@ref)
