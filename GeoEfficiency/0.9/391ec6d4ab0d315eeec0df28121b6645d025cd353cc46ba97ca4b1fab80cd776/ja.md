```
setSrcToPoint(yes::Bool)::Bool
```

`yes` が `true` の場合は `srcType` を `srcPoint` に設定した後、ソースタイプがポイントかどうかを返します。そうでない場合、`yes` が `false` の場合は、他の非ポイントタイプ（`srcDisk`、`srcLine`、`srcVolume`）に設定されていなければ `srcNotPoint` に設定します。

!!! note
      * ユーザーはこの関数を使用して、いつでもソースタイプを変更できます。
      * ソースタイプは、ソースを要求された最初の時に設定されます。


**see also:** [`typeofSrc(::Int)`](@ref).
