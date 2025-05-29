```
@req(assert, msg)
@req assert msg
```

アサーション `assert` が真であるかどうかを確認します。そうでない場合、エラーメッセージ `msg` を持つ `ArgumentError` をスローします。

マクロ `@req` は2つの引数を取ります。最初の引数はアサーション `assert`（ブール値を返す式）であり、2番目の引数は `assert` が偽のときに返されるエラーメッセージに対応する文字列 `msg` です。

引数の数が2でない場合、`AssertionError` が発生します。

# 例

```jldoctest
julia> function req_test(x::Int)
       @req iseven(x) "x must be even"
       return div(x,2)
       end
req_test (generic function with 1 method)

julia> try req_test(3)
       catch e e
       end
ArgumentError("x must be even")

julia> try req_test(2)
       catch e e
       end
1

```
