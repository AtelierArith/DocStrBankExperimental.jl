```
add_useful_columns(linked_data::AbstractDataFrame, linking_settings::NamedTuple)
```

リンク後、データフレームにいくつかの有用な列を追加します。例えば、dx、dy、dp（速度）、およびマイクロメートル単位のサイズ測定を含みます。

[`numerical_derivative`](@ref) および [`total_displacement`](@ref) 関数を使用します。

# 定義

  * `particle_unique` : 粒子を一意に識別する文字列。これはファイル名と粒子番号の組み合わせです。
  * `dx` : `x` の数値微分、すなわち x 方向の瞬時速度。単位はピクセル/フレーム。
  * `dy` : `y` の数値微分、すなわち y 方向の瞬時速度。単位はピクセル/フレーム。
  * `dp` : 瞬時速度。√(dx^2 + dy^2)。単位はピクセル/フレーム。
  * `dx_um` : µm/s に変換された dx。
  * `dy_um` : µm/s に変換された dy。
  * `dp_um` : µm/s に変換された dp。
  * `total_displacement_um` : マイクロボットの総移動量。これは合計であるため、すべての行で一定です。単位は µm。
  * `Area_um` : マイクロボットの面積。単位は µm^2。
  * `time` : フレーム列から変換された時間。単位は秒。
  * `Major_um` : マイクロボットのフィットした楕円の主軸。単位は µm。
  * `Minor_um` : マイクロボットのフィットした楕円の副軸。単位は µm。
