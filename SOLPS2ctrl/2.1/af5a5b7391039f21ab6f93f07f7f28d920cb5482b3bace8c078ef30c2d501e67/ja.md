```
mesh_psi_spacing(
    dd::IMAS.dd;
    eq_time_idx::Int=1,
    eq_profiles_2d_idx::Int=1,
    grid_ggd_idx::Int=1,
    space_idx::Int=1,
    avoid_guard_cell::Bool=true,
    spacing_rule="mean",
)
```

メッシュを検査して、psi_Nでの面の間隔を確認します。GGDと平衡が充填されている必要があります。

入力引数:

  * `dd`: 必要なデータがロードされたデータ辞書インスタンス
  * `eq_time_idx`: 使用する平衡時間スライスのインデックス。典型的なSOLPS実行では、SOLPSメッシュは単一の時間での平衡再構成に基づいているため、SOLPS実行に関連付けられたDDには1つの平衡時間スライスのみをロードする必要があります。ただし、完全な平衡時間系列をSOLPS実行と組み合わせることができ、その場合はSOLPSメッシュに対応する平衡のスライスを指定する必要があります。
  * `eq_profiles_2d_idx`: 平衡`time_slice`の`profiles_2D`のインデックス。
  * `grid_ggd_idx`: 使用する`grid_ggd`のインデックス。典型的なSOLPS実行では、SOLPSグリッドは固定されているため、このインデックスはデフォルトで1になります。しかし、将来的に時間変化するグリッドが使用される場合、このインデックスを指定する必要があります。
  * `space_idx`: 使用するスペースのインデックス。典型的なSOLPS実行では、スペースは1つだけなので、このインデックスはほとんどの場合1のままです。
  * `avoid_guard_cell`: 最後のセルがガードセルであると仮定し、`end-2`と`end-1`を使用する代わりに`end`と`end-1`を使用します。
  * `spacing_rule`: 新しいセルの間隔（`psi_N`内）がメッシュの端の間隔と同じになるようにするための"edge"または、平均間隔と同じになるようにするための"mean"。
