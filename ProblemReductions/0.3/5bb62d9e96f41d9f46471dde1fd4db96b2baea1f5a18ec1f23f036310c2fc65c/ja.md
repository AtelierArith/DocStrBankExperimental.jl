```
ConstraintSatisfactionProblem{T} <: AbstractProblem
```

制約充足問題の抽象基底型です。`T`は制約のローカルサイズの型です。

### 必要なインターフェース

  * [`constraints`](@ref)、制約の仕様。制約が違反されると、サイズは無限大になります。
  * [`objectives`](@ref)、重み付けに関連するソフト制約としてのサイズ項の仕様。

### オプションのインターフェース

  * [`weights`](@ref): ソフト制約の重み。
  * [`set_weights`](@ref): `problem`の重みを変更し、新しい問題インスタンスを返します。

### 派生インターフェース

  * [`is_satisfied`](@ref)、制約が満たされているかどうかを確認します。
