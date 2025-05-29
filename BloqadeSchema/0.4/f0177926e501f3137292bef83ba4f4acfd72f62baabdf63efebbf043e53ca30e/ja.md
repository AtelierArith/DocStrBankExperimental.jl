```
to_schema(h::BloqadeExpr.RydbergHamiltonian; nshots::Int, device_capabilities::DeviceCapabilities=get_device_capabilities())
to_schema(h::BloqadeExpr.RydbergHamiltonian, params::SchemaTranslationParams)
```

`h`を`params`を持つ`QuEraTaskSpecification`インスタンスに変換します。paramsが明示的に構築されていない場合、`nshots`と`device_capabilities`から自動的に構築されます。

`h`がマシンで実行可能であることを確認するために検証が行われます。これにより、違反が検出された場合に例外がスローされる可能性があります。以下のログ/警告/例外を参照してください。

# ログ/警告/例外

`device_capabilities`の違反が検出された場合、`ValidationException`がスローされ、[`ValidationViolations`](@ref)インスタンスがラップされます。

違反には以下が含まれます：

## 波形タイプ

  * ϕは`PiecewiseConstantWaveform`型ではありません
  * ΩとΔは`PiecewiseLinearWaveform`型ではありません

## 原子位置

  * 要求されたキュービットの数がデバイスがサポートする数を超えています
  * 原子の位置がデバイスがサポートする位置解像度を超えています
  * 原子配置の全幅/高さがデバイスがサポートするものを超えています
  * 原子間の垂直行間隔がデバイスがサポートするものより小さいです
  * 原子間の半径間隔がデバイスがサポートするものより小さいです

## 一般的な波形制約（Ω、Δ、ϕに適用）

  * 持続時間がデバイスがサポートする持続時間を超えています
  * 持続時間がデバイスがサポートする最小時間ステップより小さいです
  * 最小時間ステップがサポートされている最小時間ステップより小さいです
  * 値がサポートされている最小値より小さいです
  * 値がサポートされている最大値より大きいです

## Ω波形特有の制約

  * 勾配がサポートされている最大勾配を超えています
  * 開始値と終了値が0.0 rad/μsに等しくありません

## Δ波形特有の制約

  * 勾配がサポートされている最大勾配を超えています

## ϕ波形特有の制約

  * 開始値が0.0 rad/μsに等しくありません

## その他の違反

  * ショット数がサポートされている最小数を下回っています
  * ショット数がサポートされている最大数を超えています

```
