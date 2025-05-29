```
Styles(css::CSS...)
```

Stylesオブジェクトを作成します。これはCSSオブジェクトのセットを表します。StylesオブジェクトをDOMノードに挿入すると、`<style>`ノードとしてレンダリングされます。これを直接`DOM.div(style=Style(...))`に割り当てると、特定のdivにスタイリングが適用されます。`Session`ごとに、すべての`Styles`内のユニークなcssオブジェクトはセッション全体で一度だけレンダリングされることに注意してください。これにより、コンポーネント内でスタイリングを簡単に作成でき、ページ上に多くのStyleノードを作成することを心配する必要がなくなります。`Styles`を少し使いやすくするための便利なコンストラクタが2つあります：

```julia
Styles(pairs::Pair...) = Styles(CSS(pairs...))
Styles(priority::Styles, defaults...) = merge(Styles(defaults...), priority)
```

コンポーネントのスタイリングには、常にユーザーがStyleのカスタマイズをマージできるようにすることをお勧めします。このように：

```julia
function MyComponent(; style=Styles())
    return DOM.div(style=Styles(style, "color" => "red"))
end
```

すべてのBonitoコンポーネントはこの方法でスタイリング可能です。

!!! info
    なぜ`Hyperscript.Style`ではないのか？`Hyperscript.Style`によるスコープ付きスタイリングは素晴らしいですが、セッション全体でCSSオブジェクトの重複排除を許可しないため、スタイリング可能なコンポーネントを作成するのが難しくなります。また、重複排除に特化していないため、かなり遅くなりますし、キャメルケースのキーワードからCSS属性への変換は非常にコストがかかります。これが、`CSS`がキーワード引数の代わりに文字列のペアを使用する理由でもあります。

