```
getresponse!( chat::Chat
            , maxrequests::Int=1
            , compact::Bool=true
            , model::AbstractString="gpt-3.5-turbo"
            , options...)::Resp
```

OpenAI APIから応答を取得し、チャットログに追加します。
