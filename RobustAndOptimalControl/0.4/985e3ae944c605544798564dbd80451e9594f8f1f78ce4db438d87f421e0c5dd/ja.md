```
passivityplot(sys, args...; hz=false)
passivityplot(LTISystem[sys1, sys2...], args...; hz=false)
```

`LTISystem`(s)のパッシビティインデックスをプロットします。インデックスが < 0 の周波数ではシステムはパッシブです。

周波数ベクトル `w` をオプションで提供できます。

`hz=true` の場合、プロットのx軸はヘルツで表示され、入力周波数ベクトルは依然としてrad/sとして扱われます。

`kwargs` は `Plots.plot` への引数として送信されます。

詳細については [`passivity_index`](@ref) を参照してください。また、[`ispassive`](@ref)、[`passivity_index`](@ref) も参照してください。
