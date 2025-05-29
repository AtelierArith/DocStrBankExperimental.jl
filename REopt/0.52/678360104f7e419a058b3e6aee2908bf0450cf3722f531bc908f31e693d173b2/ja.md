```
cambium_profile(; scenario::String, 
                            location_type::String, 
                            latitude::Real, 
                            longitude::Real,
                            start_year::Int,
                            lifetime::Int,
                            metric_col::String,
                            grid_level::String,
                            time_steps_per_hour::Int=1,
                            load_year::Int=2017,
                            profile_year::Int=2017,
                            )
```

この関数は、提供された `metric_col` に応じて、排出データまたはクリーンエネルギー割合データを取得するために、CambiumデータベースへのAPIリクエストを構築します。データは、提供された「ライフタイム」にわたって時間単位で平均化されます。返されるプロファイルは、提供された「ロード年」との曜日の整合性に調整されます（Cambiumプロファイルは常に日曜日から始まります）。

この関数は、特にグリッド排出データを表示するためのウェブツールにおいて、REopt APIの /cambium_profile エンドポイントでも使用されます。
