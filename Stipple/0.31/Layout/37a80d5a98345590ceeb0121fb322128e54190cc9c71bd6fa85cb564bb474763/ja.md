```
@gutter(size, children)
```

子要素の間隔を設定します。（例として `StippleUI` の `card()` と `prettify()` を使用します。）

```julia
julia> row(@gutter :md [
         card("Hello", sm = 12, lg = 4)
         card("World", sm = 12, md = 8)
       ]) |> prettify |> println
<div class="row col q-col-gutter-md">
    <div class="col col-sm-12 col-lg-4">
        <q-card>
            Hello
        </q-card>
    </div>
    <div class="col col-sm-12 col-md-8">
        <q-card>
            World
        </q-card>
    </div>
</div>
```

このマクロの内部的な理由は、ガター内の要素は上記のように div 要素でラップする必要があるためです。

# 注意点

このマクロは、子要素がコマンド内に明示的に書かれている場合にのみ処理できます。マクロは変数の内容を処理できないため、`row(@gutter [c1, c2])` は失敗します。

代わりに、ガターのマクロを c1 の定義に移動し、ガターサイズを親要素に渡します。

```
c1 = @gutter card("Hello", sm = 2,  md = 8)
c2 = @gutter card("World", sm = 10, md = 4)

row(gutter = :md, [c1, c2])
```

異なるコンテキストで c1 をラップせずに使用する必要がある場合は、手動でラップすることになります。混合アプローチを取ることもできます。

```
c1 = card("Hello", sm = 2,  md = 8)
row(gutter = :md, [
    cell(c1, sm = 12, md = 8, lg = 4, xl = 12)
    @gutter card("World", sm = 12, md = 8, lg = 4, xl = 12)
])
```

Julia マクロ言語の制約により、マクロは式の最初の位置に置く必要があります。したがって、

```julia
row(class = "myclass", @gutter(:md, [
    card("Hello", sm = 2,  md = 8)
    card("World", sm = 10, md = 4)
])
```

は失敗します。

代わりにクラスを第二引数として置きます。

```julia
row(@gutter(:md, [
    card("Hello", sm = 2,  md = 8)
    card("World", sm = 10, md = 4)
], class = "myclass"))
```
