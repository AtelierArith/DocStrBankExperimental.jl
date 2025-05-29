```
populate_part_geometry!(model,frontier=Set(collect(part_keys(model))))
```

すべてのジオメトリを `model.parts` にロードします。ロードは再帰的であり、ジオメトリは任意のレベルのネストされたサブパーツを通じてロードされ、最終的にはメインモデルによって参照される各原子パーツに格納されます。
