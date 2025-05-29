```
AbstractElement
```

抽象データ型。要素型 `MyElement` は `AbstractElement` のサブタイプとして宣言されなければなりません。

`MyElement` は次のインターフェースを持つコンストラクタを提供しなければなりません。

```
`eleobj = MyElement(nod::Vector{Node}; kwargs...)`
```

参照: [`coord`](@ref), [`Node`](@ref), [`lagrangian`](@ref)    
