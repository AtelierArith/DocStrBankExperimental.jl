```
validate(H::BloqadeExpr.RydbergHamiltonian;device_capabilities::DeviceCapabilities=get_device_capabilities())
```

`H`が内部スキーマの一部として表現可能であるかどうか、また`device_capabilities`を介して機械が実行できる能力に該当するかどうかを確認します。

各フィールドに、`H`のどの部分に対してどの制約が違反されたかを示す文字列のセットを含む[`ValidationViolations`](@ref)を返します。

違反には以下が含まれます：

## 波形タイプ

  * ϕは`PiecewiseConstantWaveform`型ではありません
  * ΩとΔは`PiecewiseLinearWaveform`型ではありません

## 原子位置

  * 要求されたキュービットの数がデバイスがサポートする数を超えています
  * 原子の位置がデバイスがサポートする位置解像度を超えています
  * 原子配置の全幅/高さがデバイスがサポートするものを超えています
  * 原子間の半径間隔がデバイスがサポートするものより小さいです
  * 原子間の垂直行間隔がデバイスがサポートするものより小さいです

## 一般的な波形制約（Ω、Δ、ϕに適用）

  * 持続時間がデバイスがサポートする持続時間を超えています
  * 持続時間がデバイスがサポートする最小時間ステップより小さいです
  * 最小時間ステップがサポートされている最小時間ステップより小さいです
  * 値がサポートされている最小値より小さいです
  * 値がサポートされている最大値より大きいです

## Ω波形特有の制約

  * 傾きがサポートされている最大傾きを超えています
  * 開始値と終了値が0.0 rad/μsに等しくありません

## Δ波形特有の制約

  * 傾きがサポートされている最大傾きを超えています

## ϕ波形特有の制約

  * 開始値が0.0 rad/μsに等しくありません

# ログ/警告/例外

以下の例外がスローされる可能性があります：

  * ϕは`PiecewiseConstantWaveform`型ではありません
  * ΩとΔは`PiecewiseLinearWaveform`型ではありません

# 例

```jldoctest; setup:=(using BloqadeExpr, BloqadeWaveforms, BloqadeLattices)
julia> Δ = Ω = ϕ = sinusoidal(duration=2, amplitude=1.3*π);

julia> h = rydberg_h(atom_positions; Ω=Ω,Δ=Δ,ϕ=ϕ)

julia> transformed_h, _ = transform(h); # transformはエラー情報を返します

julia> validate(transformed_h) # `device_capabilities`引数のデフォルト値によって制約されます
次のバリデーション違反が発生しました：

1. 位置2 => (2.0, 0.0)と3 => (3.0, 0.0)の距離は1.0 μmで、最小値の4.0 μmを下回っています
2. 位置1 => (1.1, 0.0)と2 => (2.0, 0.0)の距離は0.8999999999999999 μmで、最小値の4.0 μmを下回っています
3. 位置1 => (1.1, 0.0)と3 => (3.0, 0.0)の距離は1.9 μmで、最小値の4.0 μmを下回っています
```
