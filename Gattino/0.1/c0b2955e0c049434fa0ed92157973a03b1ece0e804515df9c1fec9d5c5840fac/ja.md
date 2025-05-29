### Context <: AbstractContext

  * window::Component{:svg}
  * dim::Int64{Int64, Int64}
  * margin::Pair{Int64, Int64}

`Context`は、スケーリング関数を使用して、調査可能なSVGレイヤーを作成および描画するために`Gattino`メソッドと共に使用できます。このコンストラクタは通常直接呼び出されることはなく、代わりに`context`関数を使用します。`?context`は、コンテキストとコンテキストグループに関するより多くの情報を提供します。

##### 例

```
using Gattino

# コンテキストの使用方法
mycontext = context(500, 500) do con::Context
    Gattino.line!(con, [1, 2, 3], [1, 8, 4], "stroke" => "red", "stroke-width" => 2px)
end

# もちろん、これを行うこともできます。
con = Context()
Gattino.line!(con, [5, 1, 2], [7, 34, 5], "stroke" => "red", "stroke-width" => "10")
display(con)
```

---

##### コンストラクタ

  * Context(::Component{:svg}, margin::Pair{Int64, Int64})
  * Context(width::Int64 = 1280, height::Int64 = 720, margin::Pair{Int64, Int64} = 0 => 0)
