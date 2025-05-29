`v-for` ディレクティブは、配列に基づいてアイテムのリストをレンダリングするために生成されます。 [https://vuejs.org/v2/guide/list.html#Mapping-an-Array-to-Elements-with-v-for](https://vuejs.org/v2/guide/list.html#Mapping-an-Array-to-Elements-with-v-for)

`@for` は、文字列としての js 表現またはベクトルや辞書を持つ Julia 表現の両方をサポートします。

## 例

### Javascript

```julia
julia> p(" {{todo}} ", class="warning", @for("todo in todos"))
"""
<p v-for='todo in todos'>
    {{todo}}
</p>
"""
```

### Julia 表現

```julia
julia> dict = Dict(:a => "b", :c => 4);
julia> ul(li("k: {{ k }}, v: {{ v }}, i: {{ i }}", @for((v, k, i) in dict)))
"""
<ul>
    <li v-for="(v, k, i) in {'a':'b','c':4}">
        k: {{ k }}, v: {{ v }}, i: {{ i }}
    </li>
</ul>
"""
```

値、キー、インデックスの順序が Stipple のデストラクチャリングと逆になっていることに注意してください。また、`(v, k)` または `v` をループすることも可能ですが、インデックスは常にゼロベースです。
