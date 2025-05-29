```
@scenario(args..., probability = )
```

指定された確率で[`@uncertain`](@ref)宣言に一致する[`Scenario`](@ref)を作成します。

```
@scenario(var1 = val1, var2 = val2, ..., probability = 1.0)
```

`@uncertain var1, var2, ...`の形式の[`@uncertain`](@ref)注釈に一致する[`Scenario`](@ref)を作成します。

```
@scenario(ξ[i=..., j=..., ...] = values, probability = 1.0)
```

`@uncertain ξ[i=..., j=..., ...]`の形式の[`@uncertain`](@ref)注釈に一致する[`Scenario`](@ref)を作成します。`values`は指定されたインデックスセットと同じ次元でなければなりません。

```
@scenario(ξ[i=..., j=..., ...], expr, probability = 1.0, requested_container = :Auto)
```

`@uncertain ξ[i=..., j=..., ...]`の形式の[`@uncertain`](@ref)注釈に一致する[`Scenario`](@ref)を作成します。JuMPの`@container`マクロをラップして、基礎データとして`DenseAxisArray`または`SparseAxisArray`を作成します。さらなる構文情報については`@container`を参照してください。

## 例

以下は、確率$0.4$および値$[24.0 28.0 500.0 100.0]$のランダムベクトル$[q₁(ξ) q₂(ξ) d₁(ξ) d₂(ξ)]$のインスタンスを作成する同等の方法です。

```julia
@scenario q₁ = 24.0 q₂ = 28.0 d₁ = 500.0 d₂ = 100.0 probability = 0.4

@scenario ξ[i in 1:4] = [24.0, 28.0, 500.0, 100.0] probability = 0.4
```
