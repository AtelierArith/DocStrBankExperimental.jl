```
@gutter(child_or_children)
```

要素をgutterコンテナの一部としてdiv要素でラップします。（gutterサイズを設定する2引数バージョンのマクロについては、下記を参照してください。）

### 例 1

```julia
julia> @gutter [
         card("Hello", sm = 12, lg = 4)
         card("World", sm = 12, md = 8)
       ]

2-element Vector{ParsedHTMLString}:
 "<div class="col col-sm-12 col-lg-4"><q-card>Hello</q-card></div>"
 "<div class="col col-sm-12 col-md-8"><q-card>World</q-card></div>"
```

子要素はコード内で明示的に記述する必要があることに注意してください。詳細については下記を参照してください。

### 例 2

```
julia> row(gutter = :md, @gutter [
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
