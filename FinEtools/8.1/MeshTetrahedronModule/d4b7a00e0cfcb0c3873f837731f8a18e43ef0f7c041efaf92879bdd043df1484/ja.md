```
T4refine20(fens::FENodeSet, fes::FESetT4)
```

4ノードの四面体メッシュを別の4ノードの四面体メッシュに細分化します。各元の四面体は20の新しい四面体に分割されます。

各頂点には1つの六面体が与えられます。このスキームは、六面体を作成する際に各エッジごとに1つ、各面ごとに1つ、内部用に1つの合計15ノードを生成します。
