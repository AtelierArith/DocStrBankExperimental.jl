```
splitting_lax_friedrichs(u, orientation_or_normal_direction,
                         equations::CompressibleEulerEquations2D)
splitting_lax_friedrichs(u, which::Union{Val{:minus}, Val{:plus}}
                         orientation_or_normal_direction,
                         equations::CompressibleEulerEquations2D)
```

ナイーブなローカルLax-Friedrichsスタイルのフラックス分割は、`f⁺ = 0.5 (f + λ u)`および`f⁻ = 0.5 (f - λ u)`の形をしており、例えばバーガーズ方程式に適用されるフラックス分割に似ています。

負の軸方向に進む波に関連する「マイナス」フラックスと、正の軸方向に進む波に関連する「プラス」フラックスのタプルを返します。フラックスのうち一方のみが必要な場合は、引数`which`を`Val{:minus}()`または`Val{:plus}()`に設定した関数シグネチャを使用してください。

!!! warning "実験的な実装 (アップウィンドSBP)"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

