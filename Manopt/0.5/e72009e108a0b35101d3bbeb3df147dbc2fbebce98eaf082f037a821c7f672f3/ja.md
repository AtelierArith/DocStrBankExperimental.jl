```
すべてのランツォスベクトルが使用されたときに停止する <: StoppingCriterion
```

内部反復で全てのランツォスベクトルが使用された場合、この停止基準は、ベクトル用に割り当てられた配列内の存在しないフィールドにアクセスしないためのフォールバック/セキュリティ停止基準です。

この停止基準は（現時点では）[`AdaptiveRegularizationState`](@ref)を使用する[`LanczosState`](@ref)サブソルバーの場合にのみ実装されています。

# フィールド

  * `maxLanczosVectors`: ランツォスベクトルの最大数
  * `at_iteration`は、停止基準が満たされた反復（`i=0`を含む）を示し、満たされていない場合は`-1`です。

# コンストラクタ

```
StopWhenAllLanczosVectorsUsed(maxLancosVectors::Int)
```
