イベントを追跡する

# 引数

  * `analytics::Analytics`
  * `attrs::Dict`: イベントペイロード

## 可能な attrs

  * `event::String`: イベント名
  * `properties::Dict`: イベントプロパティ（オプション）
  * `anonymous_id::String`: ユーザーが誰であるかまだわからない場合のID。（オプションですが、`anonymous_id` または `user_id` のいずれかを提供する必要があります）
  * `context::Dict`: （オプション）
  * `integrations::Dict`: このイベントが送信される統合（オプション）
  * `message_id::String`: API全体でメッセージを一意に識別するID。（オプション）
  * `timestamp::Union{DateTime, ZonedDateTime}`: イベントが発生した時刻（オプション）
  * `user_id::String`: データベース内のこのユーザーのID（オプションですが、`anonymous_id` または `user_id` のいずれかを提供する必要があります）
  * `options::Dict`: ユーザーの特性などのオプション（オプション）

# 例

```julia
using SegmentAnalytics

analytics = SegmentAnalytics.Analytics(write_key="write_key")
payload = Dict(
  :event => "Event Name",
  :user_id => "User ID",
  :properties => Dict(:p1 => 1, :p2 => 2),
  :message_id => "custom-message-id"
)

track(analytics, payload)
```
