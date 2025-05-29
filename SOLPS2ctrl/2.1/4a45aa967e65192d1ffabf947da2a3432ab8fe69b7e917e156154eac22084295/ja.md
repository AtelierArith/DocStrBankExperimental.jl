```
cached_mesh_extension!(
    dd::IMAS.dd,
    eqdsk_file::String,
    b2fgmtry::String;
    eq_time_idx::Int=1,
    eq_profiles_2d_idx::Int=1,
    grid_ggd_idx::Int=1,
    space_idx::Int=1,
    clear_cache::Bool=false,
)::String
```

データ辞書に拡張メッシュを追加します。キャッシュされた結果からの可能性があります。

入力引数:

  * `dd`: データ辞書。インプレースで変更されます。
  * `eqdsk_file`: dd内の平衡データを取得するために使用されたEQDSKファイルの名前。
  * `b2fgmtry`: dd内の`edge_profiles`でGGD情報を取得するために使用されたSOLPSジオメトリファイルの名前。
  * `eq_time_idx`: 平衡における時間スライスのインデックス
  * `eq_profiles_2d_idx`: 平衡における2Dプロファイルセットのインデックス（通常は1つだけです）
  * `grid_ggd_idx`: edge*profiles内の`grid*ggd`セットのインデックス
  * `space_idx`: 空間のインデックス
  * `clear_cache`: 既存のキャッシュファイルを削除します（テスト用）
