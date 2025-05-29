```
receive(lk; timeout=5.0)
receive(lk, from; timeout=5.0)
receive(lk, M; timeout=5.0)
receive(lk, M, from; timeout=5.0)
```

リンク `lk` を介してメッセージを受信します。

`M` または `from` が提供されている場合、`receive` は一致するメッセージのみを返します。`lk` 内の他のメッセージは、以前の順序で復元されます。

# パラメータ

  * `lk::Link`: メッセージが受信されるローカルまたはリモートリンク、
  * `M::Type{<:Msg}`: [`Msg`](@ref) タイプ、
  * `from::Link`: 送信者のローカルまたはリモートリンク。`from` が提供されている場合、`from` フィールドを持つメッセージのみが一致します。
  * `timeout::Real=5.0`: 最大待機時間（秒）。

      * `timeout==0` の場合、`lk` は既存のメッセージのみをスキャンします。
      * タイムアウトを望まない場合は、`timeout=Inf` に設定します。

# 戻り値

  * 受信したメッセージまたは `Timeout()`。
