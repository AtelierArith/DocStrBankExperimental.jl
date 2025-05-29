```
AnsiTextCell(string::AbstractString)
```

`string`を使用して[`AnsiTextCell`](@ref)を作成します。

```
AnsiTextCell(renderfn[; context])
```

レンダリング関数を使用して[`AnsiTextCell`](@ref)を作成します。

`renderfn`は次のシグネチャを持つ関数です：

```
renderfn(io)::String
```

ANSIシーケンスを含む可能性のある文字列を`io`にレンダリングします。

`context`は、`renderfn`が受け取る`IOContext`に渡されるコンテキスト引数のタプルです。利用可能な引数の詳細については`IOContext`を参照してください。

リッチな端末出力を持つパッケージをサポートするのに便利です。

## 例

以下は、リッチなデータをリッチな端末出力を持つパッケージを利用してテーブルに印刷するための`AnsiTextCell`のラッパーの例です。

### Crayons.jl

セル内のテキストにカスタム装飾を適用します。

```julia
using Crayons, PrettyTables

b = crayon"blue bold"
y = crayon"yellow bold"
g = crayon"green bold"

pretty_table([AnsiTextCell("$(g)This $(y)is $(b)awesome!") for _ in 1:5, _ in 1:5])
```

### ImageInTerminal.jl

テーブル内に画像を表示します。

```julia
using ImageInTerminal, PrettyTables

function ImageCell(img, size)
    return AnsiTextCell(
        io -> ImageInTerminal.imshow(io, img),
        context = (:displaysize => size,)
    )
end

using TestImages
img = testimage("lighthouse")
pretty_table([ImageCell(img, (20, 20)) ImageCell(img, (40, 40))])
```

### UnicodePlots.jl

テーブル内にさまざまなプロットを表示します。

```julia
using UnicodePlots, PrettyTables

function UnicodePlotCell(p)
    return AnsiTextCell(
        io -> show(io, p),
        context = (:color => true,)
    )
end

pretty_table([
    UnicodePlotCell(barplot(Dict("x" => 10, "y" => 20)))
    UnicodePlotCell(boxplot([1, 3, 3, 4, 6, 10]))
])
```

### CommonMark.jl

テーブル内でリッチなMarkdownを使用します。

```julia
using CommonMark, PrettyTables

function MarkdownCell(md)
    return AnsiTextCell(
        renderfn = io -> display(TextDisplay(io), md),
        context = (:color => true,)
    )
end

pretty_table([MarkdownCell(cm"**Hi**") MarkdownCell(cm"> quote")])
```
