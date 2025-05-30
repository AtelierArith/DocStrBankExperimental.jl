```
GeneratedField(d::GridData,field::AbstractSpatialField...,grid::PhysicalGrid)
```

スカラーグリッドデータ `d` に基づいて、グリッド `grid` 上に空間フィールド関数 `field` のインスタンスを作成します。インスタンス `g = GeneratedField(d,field,grid)` を作成した後、結果のグリッドデータには `g()` と入力することでアクセスできます。ベクトルグリッドデータの場合、各コンポーネントに対して別々の `field` を指定する必要があります。

フィールドが時間依存の場合、希望する時間で `g(t)` を評価することもできます。フィールドが静的な場合、時間引数は無視されます。
