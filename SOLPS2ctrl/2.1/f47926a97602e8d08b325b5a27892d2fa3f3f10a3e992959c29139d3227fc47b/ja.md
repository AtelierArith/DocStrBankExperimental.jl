```
fill_in_extrapolated_core_profile!(
    dd::IMAS.dd,
    quantity_name::String;
    method::String="simple",
    eq_time_idx::Int=1,
    eq_profiles_2d_idx::Int=1,
    grid_ggd_idx::Int=1,
    space_idx::Int=1,
)
```

この関数は、`equilibrium`および`edge_profiles`で埋めるべきDDと、コアに外挿する量のリクエストを受け入れます。次に、`edge_profiles`データをrhoにマッピングし、外挿を実行する関数を呼び出します（これは単純な線形外挿ではなく、やや説得力のあるプロファイル形状を作成しようとするトリックがあります）し、結果をcore_profilesに書き込みます。これには多くの補間などが含まれます。

入力引数：

  * `dd`: IMASデータ辞書
  * `quantity_name`: `edge_profiles.profiles_2d`および`core_profiles.profiles_1d`内の量の名前、例えば「electrons.density」
  * `method`: 外挿方法。
  * `eq_time_id`x: 使用する平衡時間スライスのインデックス。典型的なSOLPS実行の場合、SOLPSメッシュは単一の時間での平衡再構成に基づくため、SOLPS実行に関連付けられたDDは1つの平衡時間スライスのみをロードする必要があります。ただし、完全な平衡時間系列をSOLPS実行と組み合わせることができ、その場合はSOLPSメッシュに対応する平衡のスライスを指定する必要があります。
  * `eq_profiles_2d_idx`: 平衡`time_slice`内の`profiles_2D`のインデックス。
  * `grid_ggd_idx`: 使用する`grid_ggd`のインデックス。典型的なSOLPS実行の場合、SOLPSグリッドは固定されているため、このインデックスはデフォルトで1になります。しかし、将来的に時間変化するグリッドが使用される場合、このインデックスを指定する必要があります。
  * `space_id`x: 使用するスペースのインデックス。典型的なSOLPS実行の場合、スペースは1つだけなので、このインデックスはほとんどの場合1のままです。
  * `cell_subset_idx`: 外挿に使用するセルのサブセットのインデックス。デフォルトは5で、すべてのセルのサブセットです。`edge_profiles`データが別のサブセット、例えば-5（b2.5セルのみ）に対して存在する場合、このインデックスは-5に設定する必要があります。
