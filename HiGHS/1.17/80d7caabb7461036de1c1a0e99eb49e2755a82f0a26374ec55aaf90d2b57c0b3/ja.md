```
Highs_getDualRay(highs, has_dual_ray, dual_ray_value)
```

プライマル非可行性の証明である双対レイが現在存在するかどうかを示し、存在しない場合は（LPを解く代償として）それを取得します。ただし、dual*ray*valueがnullptrでない場合に限ります。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `has_dual_ray`: 双対レイが現在存在する場合は1を格納するintへのポインタ。
  * `dual_ray_value`: 無限大のレイで満たされた長さ[num_row]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
