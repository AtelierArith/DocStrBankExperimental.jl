```
TempParams
```

Temporary parameters struct for temporal models.

| **Field**       | **Type** | **Description**                                                                                                                |
|:--------------- |:-------- |:------------------------------------------------------------------------------------------------------------------------------ |
| `σ_curriculum`  | Float64  | standard deviation threshold, only used for `model_type = :m3sc, :m3vc`                                                        |
| `l_window`      | Int64    | temporal window length, only used for `model_type = :m3w, :m3tf`                                                               |
| `window_type`   | Symbol   | type of windowing, `:sliding` for overlapping or `:contiguous` for non-overlapping, only used for `model_type = :m3w, :m3tf`   |
| `tf_layer_type` | Symbol   | transformer normalization layer before or after skip connection {`:prelayer`,`:postlayer`}, only used for `model_type = :m3tf` |
| `tf_norm_type`  | Symbol   | normalization for transformer encoder {`:batch`,`:layer`,`:none`}, only used for `model_type = :m3tf`                          |
| `dropout_prob`  | Float64  | dropout rate, only used for `model_type = :m3w, :m3tf`                                                                         |
| `N_tf_head`     | Int64    | number of attention heads, only used for `model_type = :m3tf`                                                                  |
| `tf_gain`       | Float64  | weight initialization parameter, only used for `model_type = :m3tf`                                                            |
