```
with_logabsdet_jacobian(f, x)
```

変換 `f` の下での `x` の変換された値と [体積要素](https://en.wikipedia.org/wiki/Volume_element) の対数を計算します。

`(y, ladj) = with_logabsdet_jacobian(f, x)` の場合、以下が成り立つ必要があります：

  * `y == f(x)`
  * `ladj` は `log(abs(det(jacobian(f, x))))` です。

`with_logabsdet_jacobian` は、ブロードキャストされた/マップされた関数（`Base.Broadcast.BroadcastFunction` または `Base.Fix1` を介して）および `ComposedFunction` をサポートしています。

体積要素が定義されていない/適用できない場合、`with_logabsdet_jacobian(f::F, x::T)` は [`NoLogAbsDetJacobian{F,T}()`](@ref) を返します。

# 例

```jldoctest a
using ChangesOfVariables

foo(x) = inv(exp(-x) + 1)

function ChangesOfVariables.with_logabsdet_jacobian(::typeof(foo), x)
    y = foo(x)
    ladj = -x + 2 * log(y)
    (y, ladj)
end

x = 4.2
y, ladj_y = with_logabsdet_jacobian(foo, x)

using LinearAlgebra, ForwardDiff
y == foo(x) && ladj_y ≈ log(abs(ForwardDiff.derivative(foo, x)))

# 出力

true
```

```jldoctest a
X = rand(10)
broadcasted_foo = if VERSION >= v"1.6"
    Base.Broadcast.BroadcastFunction(foo)
else
    Base.Fix1(broadcast, foo)
end
Y, ladj_Y = with_logabsdet_jacobian(broadcasted_foo, X)
Y == broadcasted_foo(X) && ladj_Y ≈ logabsdet(ForwardDiff.jacobian(broadcasted_foo, X))[1]

# 出力

true
```

```jldoctest a
VERSION < v"1.6" || begin # ∘ のサポートには Julia >= v1.6 が必要です
    z, ladj_z = with_logabsdet_jacobian(log ∘ foo, x)
    z == log(foo(x)) && ladj_z == ladj_y + with_logabsdet_jacobian(log, y)[2]
end

# 出力

true
```

with*logabsdet*jacobian の実装は [`ChangesOfVariables.test_with_logabsdet_jacobian`](@ref) を使用して（`Test.@testset` として）テストできます。
