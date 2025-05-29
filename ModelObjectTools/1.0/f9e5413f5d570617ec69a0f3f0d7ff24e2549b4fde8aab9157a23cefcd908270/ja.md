showModelObject(mo)

モデルオブジェクト mo の理解しやすい表現を表示し、同一のオブジェクトを構築するためのコマンドとして使用できる（デフォルトコンストラクタが利用可能な場合）。

# 例

```julia-repl

julia> struct ExStr
       a::Float64
       vec::Tuple{Float64, Float64, Float64}
       end

julia> s = ExStr(3.0, (1.0,2.0,10.0))
ExStr(3.0, (1.0, 2.0, 10.0))

julia> showModelObject(s)
modelObjectFromAnother(ExStr(), 
                           :a => 3.0, 
                         :vec => (1.0, 2.0, 10.0))
```
