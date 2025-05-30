```
autolimits!(ax::PolarAxis[, unlock_zoom = true])
```

これを呼び出すと、PolarAxisはプロットされたデータから自由に制限を導出するようになり、rmin > 0およびthetalimitsが完全な円未満にまたがることを許可します。`unlock_zoom = true`の場合、これはrおよびtheta方向のズームを解除し、r方向の移動を可能にします。
