# `Makie`におけるプロットレシピ

レシピには2種類あります。*タイプレシピ*は、ユーザー定義のタイプから既存のプロットタイプへの単純なマッピングを定義します。*フルレシピ*は、テーマをカスタマイズし、カスタムプロット関数を定義できます。

## タイプレシピ

タイプレシピは非常にシンプルで、引数変換パイプラインをオーバーロードするだけです。これはすべてのプロットタイプまたはプロットタイプのサブセットに対して行うことができます：

```
# すべてのプロットタイプ
convert_arguments(P::Type{<:AbstractPlot}, x::MyType) = convert_arguments(P, rand(10, 10))
# 散布図のみに対して
convert_arguments(P::Type{<:Scatter}, x::MyType) = convert_arguments(P, rand(10, 10))
```

オプションで、`plot(x::MyType)`がこれを使用するようにデフォルトのプロットタイプを定義できます：

```
plottype(::MyType) = Surface
```

## `@recipe`マクロを使用したフルレシピ

`MyPlot`のフルレシピは2つの部分から成ります。最初はプロットタイプ名、引数、およびテーマ定義で、これは`@recipe`マクロを使用して定義されます。2番目は、原子プロット関数に基づいて実装された`MyPlot`のカスタム`plot!`です。

これがどのように機能するかを示すために例を使用します：

```
# 引数 (x, y, z) && テーマはオプション
@recipe(MyPlot, x, y, z) do scene
    Attributes(
        plot_color = :red
    )
end
```

このマクロは複数のものに展開されます。まず、型定義：

```
const MyPlot{ArgTypes} = Plot{myplot, ArgTypes}
```

`Plot`の型パラメータには、例えばシンボルの代わりに関数が含まれます。このようにして、`MyPlot`から`myplot`へのマッピングはより安全でシンプルになります。（欠点は、常に関数`myplot`が必要になることです - TODO: これは問題ですか？）

`MyPlot`を使いやすくするために、次のシグネチャが定義されます：

```
myplot(args...; kw_args...) = ...
myplot!(scene, args...; kw_args...) = ...
myplot(kw_args::Dict, args...) = ...
myplot!(scene, kw_args::Dict, args...) = ...
# など（どのシグネチャがあるかは100%確定していない）
```

レシピマクロに引数リスト`(x,y,z)`が提供されると、`argument_names`の特化が発生します：

```
argument_names(::Type{<: MyPlot}) = (:x, :y, :z)
```

これはオプションですが、例えば`plot_object = myplot(rand(10), rand(10), rand(10))`の呼び出しから最初の引数を取得するために`plot_object[:x]`を使用できるようになります。あるいは、常に`plot_object[i]`を使用して`i`番目の引数を取得できます。また、`(x,y,z)`を省略すると、`argument_names`のデフォルトバージョンが`plot_object[:arg1]`などを提供します。

`@recipe`呼び出しの本体で与えられたテーマは、`MyPlot`をプロットする任意のシーンにテーマを挿入する`default_theme`の特化に挿入されます：

```
function default_theme(scene, ::MyPlot)
    Attributes(
        plot_color = :red
    )
end
```

`MyPlot`を定義するための2番目の部分として、`plot!`を特化させて`MyPlot`オブジェクトの実際のプロットを実装する必要があります：

```
function plot!(plot::MyPlot)
    # 通常のプロットコード、以前に定義されたレシピや原子プロット操作に基づいて構築し、結合された`plot`に追加します：
    lines!(plot, rand(10), color = plot[:plot_color])
    plot!(plot, plot[:x], plot[:y])
    plot
end
```

ここで、`myplot`に供給される引数*タイプ*に応じて特化を追加することが可能です。例えば、`a`が浮動小数点数の3D配列であるときの`myplot(a)`の動作を特化させるために：

```
const MyVolume = MyPlot{Tuple{<:AbstractArray{<: AbstractFloat, 3}}}
argument_names(::Type{<: MyVolume}) = (:volume,) # 再びオプション
function plot!(plot::MyVolume)
    # 完全に透明からplot_colorまでのカラーマップでボリュームをプロットします
    volume!(plot, plot[:volume], colormap = :transparent => plot[:plot_color])
    plot
end
```

レシピに与えられたドキュメント文字列は、生成される関数に転送されます。
