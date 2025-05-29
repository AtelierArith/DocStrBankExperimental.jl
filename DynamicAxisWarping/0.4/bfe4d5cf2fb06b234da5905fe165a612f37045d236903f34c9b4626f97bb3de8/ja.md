```
matchplot2
```

`matchplot`と同様ですが、2Dおよび3D信号で動作します。

### 入力

#### 位置引数

利用可能な位置引数パターンについては、`DynamicAxisWarping.handleargs`を参照してください。

一般的に、ワープするための`x`および`y`信号と、オプションで`dtw_cost_matrix`入力を受け入れることができます。または、`x`および`y`信号に加えて`dtw`または`dtw_cost_matrix`出力を受け入れることができます（ワープステップをスキップします）。

#### キーワード引数

  * `transportcost` – `dtw_cost_matrix`を参照
  * `separation` – ℜⁿ内の信号間に追加される余分な分離/パディング
  * `showindex` – プロットにインデックス/"時間"軸のための軸を追加するかどうか（最後の次元に追加されます）
