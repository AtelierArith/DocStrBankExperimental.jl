```
AdjointGradient(o::Observable, targets, parameters::Vector) -> AdjointGradient
AdjointGradient(o::Observable, targets) -> AdjointGradient
```

`o`の期待値に関する`AdjointGradient`を`targets`の量子ビットに対して構築します。勾配は`parameters`に関する偏微分を計算することで求められます。`parameters`が存在しない場合、空である場合、または`["all"]`である場合、回路内のすべてのパラメータが使用されます。

`targets`は次のいずれかである可能性があります：

  * [`QubitSet`](@ref)
  * `Int`の`Vector`および/または[`Qubit`](@ref)
  * `Int`または`Qubit`

`AdjointGradient`は[`Sum`](@ref)演算子の使用をサポートしています。`o`が`Sum`である場合、`targets`はターゲット量子ビットのネストされたベクトルである必要があり、`targets`の`n`番目の項は`o`の`n`番目の項と同じ長さである必要があります。

# 例

```jldoctest
julia> α = FreeParameter(:alpha);

julia> c = Circuit([(H, 0), (H, 1), (Rx, 0, α), (Rx, 1, α)]);

julia> op = 2.0 * Braket.Observables.X() * Braket.Observables.X();

julia> c = AdjointGradient(c, op, [QubitSet(0, 1)], [α]);
```

`Sum`を使用する場合：

```jldoctest
julia> α = FreeParameter(:alpha);

julia> c = Circuit([(H, 0), (H, 1), (Rx, 0, α), (Rx, 1, α)]);

julia> op1 = 2.0 * Braket.Observables.X() * Braket.Observables.X();

julia> op2 = -3.0 * Braket.Observables.Y() * Braket.Observables.Y();

julia> c = AdjointGradient(c, op1 + op2, [QubitSet(0, 1), QubitSet(0, 2)], [α]);
```
