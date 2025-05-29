```
ERA5Dataset
```

ERA5再解析データセットの抽象スーパタイプで、以下のサブタイプがあります：

```
ERA5CDStore <: ERA5Dataset
ERA5Custom  <: ERA5Dataset
ERA5Dummy   <: ERA5Dataset
```

すべての`ERA5Dataset`タイプには、以下のフィールドが含まれています：

  * `path` : データを保存するために指定されたディレクトリ
  * `emask` : `LandSea`データセットを保存するために指定されたディレクトリ

すべての`ERA5CDStore`および`ERA5Custom`タイプには、以下の追加フィールドも含まれています：

  * `ID` : モジュールIDで、ファイル名のプレフィックスとしても機能します
  * `name` : モジュールのフルネーム
  * `start` : ダウンロード/分析が開始される日付
  * `stop` : ダウンロード/分析が終了する日付
  * `sldoi` : シングルレベルDOI（ERA5Dailyでは該当なし）
  * `pldoi` : プレッシャーレベルDOI（ERA5Dailyでは該当なし）
  * `ptype` : プロダクトタイプ（ERA5Dailyでは該当なし）、`reanalysis`に設定されています
