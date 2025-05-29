```
getresponse!( chat::Chat
            , maxrequests::Int=1
            , compact::Bool=true
            , model::AbstractString="gpt-3.5-turbo"
            , options...)::Resp
```

Get a response from OpenAI API and add it to the chat log.
