```
RecordEntryChange{T} <: RecordAction
```

イテレーション中に特定のエントリの変更を記録します

# 追加フィールド

  * `recorded_values` : 記録されたイテレーション
  * `field`           : [`AbstractManoptSolverState`](@ref) 内でアクセスできるシンボル
  * `distance`        : 2つのエントリの値の間の変更/距離を計算する関数 (p,o,x1,x2)
  * `storage`         : （少なくとも）`getproperty(o, d.field)`を保存するための[`StoreStateAction`](@ref)

# コンストラクタ

```
RecordEntryChange(f::Symbol, d, a::StoreStateAction=StoreStateAction([f]))
```
