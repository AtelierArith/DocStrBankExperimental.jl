`GetSpeciesByNameCode(;name_code::String,api_key::String)`

# 説明

  * 種のIDに基づいて詳細情報を取得します。

# パラメータ

  * `name_code`: 種のID。
  * `api_key`: 登録ユーザーのためのAPIサービスキー。

# 結果

  * `result`: `GetSpeciesByNameCodeStruct`型の構造体。
  * `result.data`: JSON情報から変換された辞書。
  * `result.abstract`: 洗練されたデータフレーム。

# 例

```
using SP2000China;
your_name_code = "1ac19d0d82d84dd2900d51a742fa9296";
your_api_key = "アカウントを登録してAPIキーを取得してください";
result = GetSpeciesByNameCode(name_code=your_name_code,api_key=your_api_key);
result.data
result.abstract
```
