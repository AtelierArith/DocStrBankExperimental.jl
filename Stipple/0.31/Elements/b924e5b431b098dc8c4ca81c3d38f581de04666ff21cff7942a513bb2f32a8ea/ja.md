```
@bind(expr, [type])
```

モデルパラメータをVueコンポーネントにバインドし、`v-model`プロパティを生成し、オプションでパラメータの型を定義します。[https://vuejs.org/v2/api/#v-model](https://vuejs.org/v2/api/#v-model)

### 例

```julia
julia> input("", placeholder="Type your name", @bind(:name))
"<input placeholder="Type your name"  v-model='name' />"

julia> input("", placeholder="Type your name", @bind(:name, :identity))
"<input placeholder="Type your name"  v-model.identity='name' />"
```
