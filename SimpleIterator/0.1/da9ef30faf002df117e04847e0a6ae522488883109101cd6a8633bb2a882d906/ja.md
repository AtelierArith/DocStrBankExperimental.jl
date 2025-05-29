```
@iterfn
```

型のためのイテレータを定義します。型は、イテレータを返す[`iterator`](@ref)という名前の関数を持っている必要があります。マクロが呼び出されると、型に対するイテレーションは自動的にイテレータに対するイテレーションになります。

# 引数

  * `fundef`: 装飾される関数定義、関数名は`iterator`である必要があります。

# 例

```julia
struct MyType
    data::Vector{Int}
end

@iterfn iterator(x::MyType) = x.data

for i in MyType([1, 2, 3])
    println(i)
end
```
