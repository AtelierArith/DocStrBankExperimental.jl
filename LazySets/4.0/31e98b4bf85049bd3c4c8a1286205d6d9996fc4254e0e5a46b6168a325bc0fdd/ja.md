```
vector(rm::ResetMap)
```

リセットマップによって表されるアフィンマップ $A x + b, x ∈ X$ の $b$ ベクトルを返します。

### 入力

  * `rm` – リセットマップ

### 出力

リセットマップによって表されるアフィンマップ $A x + b, x ∈ X$ の（スパース）ベクトル。ベクトルはすべてのリセット次元のリセット値を含み、他の次元ではゼロになります。
