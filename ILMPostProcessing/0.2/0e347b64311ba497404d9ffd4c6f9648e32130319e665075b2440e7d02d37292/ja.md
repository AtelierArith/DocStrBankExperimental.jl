compute_streakline(u,v,X₀::Vector,t[;τmin = t-3.0, dtstreak=0.01,dttraj=0.001]) -> Vector, Vector

速度場 `u` と `v` に基づいて、注入点 `X₀` での時刻 `t` におけるストリークラインを計算します。ストリークラインの終点は、粒子が注入点を通過した最も早い時刻である `τmin` によって設定されます。これは、現在の時刻 `t` の3時間単位前にデフォルト設定されています。時間ステップサイズ `dtstreak` は、ストリークラインに沿って粒子がサンプリングされる頻度（すなわち、ストリークラインに沿った粒子のサンプリング間隔）を設定します。ストリークラインの x および y 座標の配列を返します。
