```
splitting_lax_friedrichs(u, orientation::Integer,
                         equations::InviscidBurgersEquation1D)
splitting_lax_friedrichs(u, which::Union{Val{:minus}, Val{:plus}}
                         orientation::Integer,
                         equations::InviscidBurgersEquation1D)
```

ナイーブなローカルLax-Friedrichsスタイルのフラックス分割は、`f⁺ = 0.5 (f + λ u)` および `f⁻ = 0.5 (f - λ u)` の形を持ち、ここで `λ = abs(u)` です。

負の軸方向に進む波に関連するフラックス「マイナス」と、正の軸方向に進む波に関連するフラックス「プラス」のタプルを返します。フラックスのうち一方のみが必要な場合は、引数 `which` を `Val{:minus}()` または `Val{:plus}()` に設定した関数シグネチャを使用してください。

!!! warning "実験的な実装 (アップウィンドSBP)"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

