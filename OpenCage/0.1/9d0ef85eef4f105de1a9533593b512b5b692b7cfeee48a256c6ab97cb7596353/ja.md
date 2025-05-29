```
OpenCage
```

[OpenCage Geocoding API](https://opencagedata.com/api)のためのJulia SDKです。

このパッケージは、OpenCage Geocoding APIへの包括的なインターフェースを提供し、前方ジオコーディング（地名/住所を座標に変換）と逆ジオコーディング（座標を地名/住所に変換）の両方を可能にします。

# 機能

  * 前方ジオコーディング（地名/住所を座標に変換）
  * 逆ジオコーディング（座標を地名/住所に変換）
  * 前方および逆ジオコーディングのための非同期API
  * 設定可能な同時実行での大規模データセットのバッチ処理
  * 包括的なエラーハンドリング
  * レート制限の検出と管理
  * すべてのOpenCage APIパラメータのサポート

# 基本的な使用法

```julia
using OpenCage

# ジオコーダーインスタンスを作成
geocoder = Geocoder()  # OPENCAGE_API_KEY環境変数を使用
# または: geocoder = Geocoder("your-api-key")

# 前方ジオコーディング
response = geocode(geocoder, "Berlin, Germany")
if !isempty(response.results)
    result = response.results[1]
    println("座標: $(result.geometry.lat), $(result.geometry.lng)")
end

# 逆ジオコーディング
response = reverse_geocode(geocoder, 52.5200, 13.4050)
if !isempty(response.results)
    result = response.results[1]
    println("住所: $(result.formatted)")
end
```

詳細な使用例については、examplesディレクトリを参照してください。
