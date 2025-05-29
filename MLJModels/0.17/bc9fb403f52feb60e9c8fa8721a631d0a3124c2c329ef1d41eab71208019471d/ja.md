```
models(; wrappers=false)
```

MLJレジストリ内のすべてのモデルをリストします。ここで、*model*は、実際のモデルタイプのためのレジストリメタデータエントリを意味します（定義コードがロードされていないタイプのプロキシ）。`TunedModel`や`Stack`などのラッパーや他の複合モデルを含めるには、`wrappers=true`を指定します。

```
models(filters...; wrappers=false)
```

各`filter`が`filter(m)`が真であるすべてのモデル`m`をリストします。

```
models(matching(X, y); wrappers=false)
```

トレーニングデータ`X`、`y`に互換性のあるすべての教師ありモデルをリストします。

```
models(matching(X); wrappers=false)
```

トレーニングデータ`X`に互換性のあるすべての教師なしモデルをリストします。

### 例

もし

```
task(model) = model.is_supervised && model.is_probabilistic
```

であれば、`models(task)`は確率的予測を行うすべての教師ありモデルをリストします。

参照: [`localmodels`](@ref).
