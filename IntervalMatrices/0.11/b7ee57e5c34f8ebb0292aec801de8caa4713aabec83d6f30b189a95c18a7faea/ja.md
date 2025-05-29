```
increment(pow::IntervalMatrixPower; [algorithm=default_algorithm])
```

`pow`を変更せずに行列の累乗を増加させます。

### 入力

  * `pow` – 行列の累乗のラッパー
  * `algorithm` – （オプション; デフォルト: `default_algorithm`）行列の累乗を計算するためのアルゴリズム; 利用可能なオプションについては[`increment!`](@ref)を参照してください

### 出力

次の行列の累乗。
