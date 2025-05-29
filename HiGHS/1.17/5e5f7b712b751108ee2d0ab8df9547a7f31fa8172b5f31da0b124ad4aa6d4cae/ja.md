```
Highs_getPrimalRay(highs, has_primal_ray, primal_ray_value)
```

プライマル無限大の証明であるプライマルレイが現在存在するかどうかを示し、存在しない場合は（LPを解く代償として）それを取得します。ただし、primal*ray*valueがnullptrでない場合に限ります。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `has_primal_ray`: プライマルレイが存在する場合は1を格納するためのintへのポインタ。
  * `primal_ray_value`: 無限大のレイで埋められた長さ[num_col]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
