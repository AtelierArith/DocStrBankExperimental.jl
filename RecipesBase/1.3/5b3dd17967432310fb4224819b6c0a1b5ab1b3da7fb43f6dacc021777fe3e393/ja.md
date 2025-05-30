この便利なマクロは、関数定義を処理し、`-->` コマンドを置き換え、引数に基づいて `RecipesBase.apply_recipe` の新しいバージョンを追加します。

この機能は、主にユーザータイプと設定を Plots.jl の視覚化を説明するデータと属性に変換することを目的としています。

`-->` コマンドを使用して属性を設定し、現在の引数を置き換えるべきカンマ区切りの引数のリストを返します。

例:

```julia
using RecipesBase

# 表示したいカスタムタイプ
struct T end

@recipe function plot(t::T, n::Integer = 1; customcolor = :green)
    markershape --> :auto, :require
    markercolor --> customcolor, :force
    xrotation --> 5
    zrotation --> 6, :quiet
    rand(10,n)
end

# ---------------------

# この例では、Plots が私たちのレシピの最終的な消費者になります
using Plots; gr()

# この呼び出しは、Plots の処理パイプラインの一部として暗黙的に `RecipesBase.apply_recipe` を呼び出します
# （Plots ドキュメントのパイプラインセクションを参照）。
# 5つの線グラフをプロットし、すべてのマーカーに黒い円を使用します。
# markershape 引数はサポートされている必要があり、zrotation 引数の警告は抑制されます。
# ユーザーは markercolor を除くすべての引数を上書きできます。
plot(T(), 5; customcolor = :black, shape=:c)
```

この例では、多くの仕組みが動作しているのがわかります。私たちは、ディスパッチに使用する新しいタイプ `T` を作成し、表示するシリーズの数を決定するために使用されるオプション引数 `n` を作成します。ユーザー定義のキーワード引数はそのまま渡され、`-->` コマンドはフラグで続けることができます：

  * quiet:   サポートされていないキーワードの警告を抑制
  * require: サポートされていない場合はエラー
  * force:   このキーワードのユーザーによる上書きを許可しない
