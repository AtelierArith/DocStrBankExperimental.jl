```
メッシュ
```

3Dメッシュを表す構造体。3つの頂点ごとに三角形を表します。三角形ごとのプロパティは配列の辞書に格納されます。

# フィールド

  * `vertices`: メッシュの頂点を含むベクトル。
  * `properties`: メッシュの追加プロパティを含む辞書（三角形ごとのプロパティの配列）。

# 例

```jldoctest
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> p = Dict{Symbol, AbstractVector}(:normal => [Vec(0.0, 0.0, 1.0)]);

julia> m = Mesh(v, p);
```
