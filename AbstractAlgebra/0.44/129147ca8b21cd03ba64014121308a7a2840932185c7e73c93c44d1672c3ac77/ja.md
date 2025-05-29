```
@attr RetType funcdef
```

このマクロは単項関数の定義に適用され、引数に基づいてその戻り値のキャッシュ（「メモ化」）を有効にします。これは、引数が属性ストレージをサポートしていることを前提としています（[`@attributes`](@ref)）を参照してください）[`get_attribute!`](@ref)を介して。

関数の名前は、基になる属性の名前として使用されます。

このマクロはキーワード引数を持つ単項関数に対しても同様に機能しますが、結果をキャッシュする際にはキーワード引数を無視します。つまり、異なるキーワード引数を持つ異なる呼び出しは、同一の（キャッシュされた）結果を返します。まだキャッシュされた結果がない場合は、指定されたキーワード引数で関数が呼び出されます。

実際には、次のようなコードを次のように変換します：

```julia
@attr RetType function myattr(obj::Foo)
   # ... 高コストの計算
   return result
end
```

本質的に次のようなものに等しいです：

```julia
function myattr(obj::Foo)
  return get_attribute!(obj, :myattr) do
    # ... 高コストの計算
    return result
  end::RetType
end
```

# 例

```jldoctest
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
