```
vertices_list(cap::Intersection)
```

二つの（多面体）集合の遅延交差の頂点のリストを返します。

### 入力

  * `cap` – 二つの（多面体）集合の交差

### 出力

二つの集合の遅延交差の頂点を含むリスト。

### 注意事項

基になる集合が多面体であり、交差が有界であると仮定します。

### アルゴリズム

`intersection`を使用して具体的な交差を計算し、その表現の頂点を取得します。
