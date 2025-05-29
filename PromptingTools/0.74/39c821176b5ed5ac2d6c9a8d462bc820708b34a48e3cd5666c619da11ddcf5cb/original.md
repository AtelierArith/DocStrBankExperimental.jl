```
UserMessageWithImages
```

A message type for user-generated text-based responses with images.  Consumed by `ai*` functions to generate responses.

# Fields

  * `content::T`: The content of the message.
  * `image_url::Vector{String}`: The URLs of the images.
  * `variables::Vector{Symbol}`: The variables in the message.
  * `name::Union{Nothing, String}`: The name of the `role` in the conversation.
