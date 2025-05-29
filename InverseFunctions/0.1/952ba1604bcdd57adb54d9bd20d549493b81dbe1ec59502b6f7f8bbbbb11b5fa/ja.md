```
inverse(f)
```

関数 `f` の逆を返します。

`inverse` は、マッピングされた関数およびブロードキャストされた関数（`Base.Broadcast.BroadcastFunction` または `Base.Fix1` を介して）と関数合成をサポートします（Julia >= 1.6 が必要です）。

# 例

```jldoctest
julia> foo(x) = inv(exp(-x) + 1);

julia> inv_foo(y) = log(y / (1 - y));

julia> InverseFunctions.inverse(::typeof(foo)) = inv_foo;

julia> InverseFunctions.inverse(::typeof(inv_foo)) = foo;

julia> x = 4.2;

julia> inverse(foo)(foo(x)) ≈ x
true

julia> inverse(inverse(foo)) === foo
true

julia> broadcast_foo = VERSION >= v"1.6" ? Base.Broadcast.BroadcastFunction(foo) : Base.Fix1(broadcast, foo);

julia> X = rand(10);

julia> inverse(broadcast_foo)(broadcast_foo(X)) ≈ X
true

julia> bar = log ∘ foo;

julia> VERSION < v"1.6" || inverse(bar)(bar(x)) ≈ x
true
```

# 実装

`inverse(::typeof(f))` の実装は以下を満たす必要があります。

  * `inverse(f)(f(x)) ≈ x` は、すべての `x` が `f` の定義域にある場合に成り立ち、かつ
  * `inverse(inverse(f))` が定義されており、`inverse(inverse(f))(x) ≈ f(x)` は、すべての `x` が `f` の定義域にある場合に成り立ちます。

あなたの実装は [`InverseFunctions.test_inverse`](@ref) で確認できます。
