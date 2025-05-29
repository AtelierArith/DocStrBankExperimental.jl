```julia
@datax
```

pgfkeysで読み取るためのデータファイルへの引数を出力します。最も効果的に使用されるのは[`datax` LaTeXパッケージ](https://ctan.org/pkg/datax)です。変数は名前または代入として提供でき、メタ引数は`:=`演算子を使用して提供されます。

メタ引数には、`Latexify.jl`および`UnitfulLatexify.jl`からのすべてのキーワード引数（例えば`unitformat := :siunitx`、`fmt := "%.2e"`）に加えて、いくつかの追加の引数が含まれます。

# メタ引数

  * `filename`: 書き込まれるファイルのパス。
  * `io`: ファイルの代わりに書き込む`IO`オブジェクト。`filename`引数を上書きします。これも`filename`も指定されていない場合は、`stdout`が使用されます。
  * `permissions`: デフォルトは`"w"`です。上書きするのではなくファイルに追加するために`"a"`として指定できます。`filename`引数がある場合にのみ意味があります。

# 例

```julia
julia> a = 2;
julia> b = 3.2u"m";
julia> @datax a b c=3*a d=27 unitformat:=:siunitx
\pgfkeyssetvalue{/datax/a}{\num{2}}
\pgfkeyssetvalue{/datax/b}{\qty{3.2}{\meter}}
\pgfkeyssetvalue{/datax/c}{\num{6}}
\pgfkeyssetvalue{/datax/d}{\num{27}}

```
