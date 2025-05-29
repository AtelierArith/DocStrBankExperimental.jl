```
increment!(pow::IntervalMatrixPower; [algorithm=default_algorithm])
```

行列の累乗をインプレースで増加させます（つまり、結果を `pow` に格納します）。

### 入力

  * `pow`       – 行列の累乗のラッパー（この関数で修正されます）
  * `algorithm` – （オプション; デフォルト: `default_algorithm`）行列の累乗を計算するためのアルゴリズム; 利用可能なオプション:

      * `"multiply"` – 前の結果から `*` を使用して高速計算
      * `"power"` – `^` を使用して再計算
      * `"decompose_binary"` – `k = 2a + b` に分解
      * `"intersect"` – `"multiply"`/`"power"`/`"decompose_binary"` の組み合わせ

### 出力

修正されたラッパーに反映された次の行列の累乗。

### 注意

`"algorithm"` に関係なく、インデックスが2の累乗である場合、平方を使用して正確な結果を計算します。
