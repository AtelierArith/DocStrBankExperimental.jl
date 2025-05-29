```
struct Platform{M,C}
  models::Dict{Symbol,M}     # モデルを格納する辞書
  scenarios::Dict{Symbol,C} # シナリオを格納する辞書
end
```

モデリングプラットフォームを表す主要なストレージ。通常、HetaSimulatorは複数のモデルとシナリオを含む1つのプラットフォームオブジェクトで動作します。

通常、`Platform`はHeta形式のファイルに基づいて[`load_platform`]{@ref}を使用して作成されます。

プラットフォームの内容を取得するには、メソッドを使用します: `models(platform)`, `scenarios(platform)`。
