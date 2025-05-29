```
AbstractMeshSearchFunction
```

呼び出し可能であるべきです `search!(problem, mesh_size, p, X; kwargs...)`

ここで `X` は、存在する場合は `p` における接空間からの最後の成功したポール方向であり、そうでない場合はゼロベクトルです。

それに加えて、以下の関数を実装する必要があります

  * `is_successful(search!)` は、最後の検索が新しい候補を見つけるのに成功したかどうかを示します
  * `get_candidate(search!)` は、最後に見つかった候補を返します
