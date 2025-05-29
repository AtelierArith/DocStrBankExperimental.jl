```
sheets_client(scopes::Union{AuthScope,Array{AuthScope,1}}; 
    rate_limiter_read::AbstractRateLimiter=default_rate_limiter_read, 
    rate_limiter_write::AbstractRateLimiter=default_rate_limiter_write)::GoogleSheetsClient
```

Google Sheetsにアクセスするためのクライアントを作成します。

# 引数

  * `scopes::Union{AuthScope,Array{AuthScope,1}}`: 認証スコープ。
  * `rate_limiter_read::AbstractRateLimiter=default_rate_limiter_read`: 読み取り用のレートリミッター。
  * `rate_limiter_write::AbstractRateLimiter=default_rate_limiter_write`: 書き込み用のレートリミッター。
