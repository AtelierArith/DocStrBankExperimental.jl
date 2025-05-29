```
@hydromodel name begin
    component1
    component2
    ...
end
```

指定された名前とコンポーネントを持つHydroModelを作成します。

# 引数

  * `name`: モデル名のシンボル
  * コンポーネントは次のものが含まれます：

      * HydroBucketインスタンス
      * フラックス定義（@hydroflux、@neuralfluxなどを使用）
      * その他のモデルコンポーネント

# 例

```julia
@hydromodel :model1 begin
    bucket1
    @neuralflux :flux1 [y] ~ chain([x1, x2])
    bucket2
end
```
