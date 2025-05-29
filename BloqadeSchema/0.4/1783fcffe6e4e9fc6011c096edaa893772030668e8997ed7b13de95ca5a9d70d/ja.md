```
to_json(h::AbstractBlock; kw...)
to_json(h::BloqadeExpr.RydbergHamiltonian,params::SchemaTranslationParams)
```

`h` と関連する `params` を JSON オブジェクトに変換します。`params` が `SchemaTranslationParams` インスタンスとして明示的に提供されていない場合、`nshots` と `device_capabilities` から自動的に構築されます。

`h` がマシンで実行可能であることを確認するために検証が行われます。これにより、違反が検出された場合に例外がスローされる可能性があります。以下のログ/警告/例外を参照してください。

# ログ/警告/例外

`ValidationException` がスローされる可能性があり、[`ValidationViolations`](@ref) インスタンスをラップします。

`ValidationViolations` には、[`to_schema`](@ref) から検出された制約違反が含まれます。

違反には以下が含まれます：

## 波形タイプ

  * ϕ は `PiecewiseConstantWaveform` 型ではありません
  * Ω と Δ は `PiecewiseLinearWaveform` 型ではありません

## 原子位置

  * 要求されたキュービットの数がデバイスがサポートする数を超えています
  * 原子の位置がデバイスがサポートする位置解像度を超えています
  * 原子配置の全幅/高さがデバイスがサポートするものを超えています
  * 原子間の半径間隔がデバイスがサポートするものより小さいです
  * 原子間の垂直行間隔がデバイスがサポートするものより小さいです

## 一般的な波形制約（Ω、Δ、ϕ に適用）

  * 持続時間がデバイスがサポートする持続時間を超えています
  * 持続時間がデバイスがサポートする最小時間ステップより小さいです
  * 最小時間ステップがサポートされている最小時間ステップより小さいです
  * 値がサポートされている最小値より小さいです
  * 値がサポートされている最大値より大きいです

## Ω 波形特有の制約

  * 勾配がサポートされている最大勾配を超えています
  * 開始値と終了値が 0.0 rad/μs ではありません

## Δ 波形特有の制約

  * 勾配がサポートされている最大勾配を超えています

## ϕ 波形特有の制約

  * 開始値が 0.0 rad/μs ではありません

## その他の違反

  * ショット数がサポートされている最小値を下回っています
  * ショット数がサポートされている最大値を超えています

# 例

```jldoctest
julia> Ω = BloqadeWaveforms.piecewise_constant(; clocks=[0, 2, 4, 6, 7], values=[5, 3, 4, 6]);

julia> Δ = BloqadeWaveforms.piecewise_linear(; clocks=[0.0, 0.6, 2.1, 2.2], values=[-10.1, -10.1, 10.1, 10.1]);

julia> ϕ = BloqadeWaveforms.piecewise_linear(; clocks=[0, 5], values=[33, 0]);

julia> atoms = [(0, 0), (1, 3), (4, 2), (6, 3), (0, 5), (2, 5)];

julia> block = BloqadeExpr.rydberg_h(atoms; Δ=Δ, Ω=Ω, ϕ=ϕ);

julia> BloqadeSchema.to_json(block; n_shots=10)
"{"nshots":10,"lattice":{"sites":[[0.0,0.0],[1.0,3.0],[4.0,2.0],[6.0,3.0],[0.0,5.0],[2.0,5.0]],"filling":[1,1,1,1,1,1]},"effective_hamiltonian":{"rydberg":{"rabi_frequency_amplitude":{"global":{"times":[0.0,-18.0,2.0,-6.0,4.0,-14.0,7.0],"values":[5.0,5.0,3.0,3.0,4.0,4.0,6.0]}},"rabi_frequency_phase":{"global":{"times":[0.0,5.0],"values":[33.0,0.0]}},"detuning":{"global":{"times":[0.0,0.6,2.1,2.2],"values":[-10.1,-10.1,10.1,10.1]}}}}}"
```
