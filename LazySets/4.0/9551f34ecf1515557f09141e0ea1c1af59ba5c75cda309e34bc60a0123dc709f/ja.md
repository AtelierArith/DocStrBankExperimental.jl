```
σ(d::AbstractVector, R::Rectification{N, <:CartesianProduct}) where {N}
```

2つの集合の直交積の直交化のサポートベクトルを返します。

### 入力

  * `d` – 方向
  * `R` – 2つの集合の直交積の直交化

### 出力

指定された方向のサポートベクトル。

### 注意事項

この実装は、新しい`Rectification`オブジェクトを作成しますが、それらは保持されません。したがって、2回目のサポートベクトルクエリは、最初のクエリの計算の恩恵を受けません。このユースケースには別の実装を追加する必要があります。

### アルゴリズム

直交化は直交積と共に分配されます。$R(·)$を集合の直交化とします。サポートベクトルを$R(X)$と$R(Y)$に対して再帰的にクエリすることができます：$σ_{R(X × Y)}(d) = σ_{R(X)}(d_X) × σ_{R(Y)}(d_Y)$、ここで$x × y$はベクトル$x$と$y$を連結します。 ```
