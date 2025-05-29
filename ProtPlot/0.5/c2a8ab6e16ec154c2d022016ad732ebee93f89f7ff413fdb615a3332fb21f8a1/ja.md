```
ribbon_scene(chain_backbones::AbstractVector{<:AbstractArray{T,3}}; backgroundcolor=:black, camcontrols=(;), kwargs...)
```

タンパク質をリボン図としてレンダリングします。表示は自動的にレンダリングされたリボンの中心に合わせられますが、ユーザーが `camcontrols` を提供した場合は別です（詳細はMakieのカメラドキュメントを参照してください）。
