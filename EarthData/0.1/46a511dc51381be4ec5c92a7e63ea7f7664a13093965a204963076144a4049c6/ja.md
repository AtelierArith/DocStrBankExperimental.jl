```
granules(; keyword=value, ...) -> Vector{Granule}
```

NASA EarthDataSearchを使用してグラニュールを検索します。可能なキーワードは `(:collection_concept_id, :granule_ur, :readable_granule_name, :online_only, :downloadable, :browsable, :attribute, :polygon, :equator_crossing_longitude, :equator_crossing_date, :updated_since, :revision_date, :created_at, :production_date, :cloud_cover, :platform, :instrument, :sensor, :project, :concept_id, :echo_granule_id, :echo_collection_id, :day_night_flag, :two_d_coordinate_system, :provider, :native_id, :short_name, :version, :entry_title, :entry_id, :temporal, :cycle, :passes, :sort_key)` または `(:page_size, :page_num, :offset, :scroll, :sort_key, :pretty, :token, :echo_compatible)` です。

```jldoctest
granules(short_name="GEDI02_A")
# output
10-element Vector{EarthData.UMM_G}:
 EarthData.UMM_G
 EarthData.UMM_G
 EarthData.UMM_G
 EarthData.UMM_G
 EarthData.UMM_G
 EarthData.UMM_G
 EarthData.UMM_G
 EarthData.UMM_G
 EarthData.UMM_G
 EarthData.UMM_G
```
