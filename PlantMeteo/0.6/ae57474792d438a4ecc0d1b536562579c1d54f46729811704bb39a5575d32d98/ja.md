```
OpenMeteo()
OpenMeteo(
    vars=PlantMeteo.DEFAULT_OPENMETEO_HOURLY,
    forecast_server="https://api.open-meteo.com/v1/forecast",
    historical_server="https://archive-api.open-meteo.com/v1/era5",
    units=OpenMeteoUnits(),
    timezone="UTC",
    models=["auto"]
)
```

[open-meteo.com](https://open-meteo.com/) APIを定義する型です。無料のためAPIキーは必要ありません。APIはAGPLライセンスの下で配布されており、商業利用には無料ではないこと、責任を持って使用する必要があることに注意してください。

# 注意事項

PlantMeteoが提供するAPIラッパーは、日次データにいくつかの変数が欠けているため、時間単位のデータにのみ対応しています。また、APIラッパーは「土壌」変数には対応していません。予測データと履歴データの間で一貫性がないためです。

# 参照

[`to_daily`](@ref)

# 引数

  * `vars`: 必要な変数、[こちら](https://open-meteo.com/en/docs)を参照してください。
  * `forecast_server`: 予測に使用するサーバー、[こちら](https://open-meteo.com/en/docs)を参照してください。デフォルトは`https://api.open-meteo.com/v1/forecast`です。
  * `historical_server`: 履歴データに使用するサーバー、[こちら](https://open-meteo.com/en/docs)を参照してください。デフォルトは`https://archive-api.open-meteo.com/v1/era5`です。
  * `start_archive::Dates.Day`: 予測サーバーの代わりに履歴アーカイブからデータを取得する最初の日、アーカイブのデータは25km解像度です。デフォルトは-150日です。
  * `units::OpenMeteoUnits`: 変数に使用される単位、[`OpenMeteoUnits`](@ref)を参照してください。
  * `timezone`: データに使用されるタイムゾーン、[こちらのリスト](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)を参照してください。

デフォルトは「UTC」です。このパラメータはチェックされないため、使用時には注意してください。

  * `models`: 予測に使用するモデル。デフォルトは`"["best_match"]"`です。詳細については[`OPENMETEO_MODELS`](@ref)を参照してください。

# トラブルシューティング

APIを呼び出す際にエラーが発生した場合は、`start_archive`の値を減少させて、例えば今日から100日前（`-Dates.Day(100)`）に設定してみてください。

# 詳細

デフォルトの変数は次のとおりです: "temperature*2m", "relativehumidity*2m", "precipitation", "surface*pressure", "windspeed*10m", "shortwave*radiation", "direct*radiation", "diffuse_radiation"。

「土壌」変数は、予測データと履歴データの間で一貫性がないため、デフォルトではダウンロードしません: "soil*temperature*0cm", "soil*temperature*6cm", "soil*temperature*18cm", "soil*temperature*54cm", "soil*moisture*0*1cm", "soil*moisture*1*3cm", "soil*moisture*3*9cm", "soil*moisture*9*27cm" および "soil*moisture*27_81cm"。

# 出典

  * [Open-Meteo.com](https://open-meteo.com/)、帰属の下で

4.0国際（CC BY 4.0）。

  * コペルニクス気候変動サービス情報2022（Hersbach et al., 2018）。

Hersbach, H., Bell, B., Berrisford, P., Biavati, G., Horányi, A., Muñoz Sabater, J., Nicolas, J.,  Peubey, C., Radu, R., Rozum, I., Schepers, D., Simmons, A., Soci, C., Dee, D., Thépaut, J-N. (2018):  ERA5の時間単位データ（単一レベル）1959年から現在まで。  コペルニクス気候変動サービス（C3S）気候データストア（CDS）。 （毎日更新）、10.24381/cds.adbb2d47
