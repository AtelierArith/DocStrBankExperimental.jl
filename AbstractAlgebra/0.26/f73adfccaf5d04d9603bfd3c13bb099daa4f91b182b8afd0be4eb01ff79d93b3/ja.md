```
@attr [RetType] funcdef
```

このマクロは単項関数の定義に適用され、引数に基づいてその戻り値のキャッシュ（「メモ化」）を有効にします。これは、引数が属性ストレージをサポートしていることを前提としています（[`@attributes`](@ref)を参照）[`get_attribute!`](@ref)を介して。

関数の名前は、基になる属性の名前として使用されます。

実際には、これを次のようなコードに変換します：

```julia
@attr function RetType myattr(obj::Foo)
   # ... 高コストの計算
   return result
end
```

これは本質的に次のようなものに等しいです：

```julia
function myattr(obj::Foo)
  return get_attribute!(obj, :myattr) do
    # ... 高コストの計算
    return result
  end::RetType
end
```

# 例

```jldoctest; setup = :(using AbstractAlgebra)
julia> @attributes mutable struct Foo
           x::Int
           Foo(x::Int) = new(x)
       end;

julia> @attr Int function myattr(obj::Foo)
                println("高コストの計算を実行中")
                return factorial(obj.x)
             end;

julia> obj = Foo(5);

julia> myattr(obj)
高コストの計算を実行中
120

julia> myattr(obj) # 2回目はキャッシュされた結果を使用
120

```
