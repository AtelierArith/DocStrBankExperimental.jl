```
SemidiscretizationEulerAcoustics(semi_acoustics::SemiAcoustics, semi_euler::SemiEuler;
                                 source_region=x->true, weights=x->1.0)
```

!!! warning "実験的なコード"
    この半離散化は実験的であり、将来のリリースで変更される可能性があります。


圧力変動方程式の半離散化を構築し、摂動した速度のソース項を介して圧縮性オイラー方程式と結合します。両方の半離散化は、同じメッシュとソルバーを使用し、共有された基底を持つ必要があります。結合領域は、単一のノードの座標を `true` または `false` にマッピングする関数 `source_region` によって説明され、ポイントが結合領域内にあるかどうかに応じて決まります。座標を重み付けにマッピングする重み関数 `weights` が音響ソース項に適用されます。この半離散化は [`EulerAcousticsCouplingCallback`](@ref) と併用する必要があり、2次元でのみ機能します。
