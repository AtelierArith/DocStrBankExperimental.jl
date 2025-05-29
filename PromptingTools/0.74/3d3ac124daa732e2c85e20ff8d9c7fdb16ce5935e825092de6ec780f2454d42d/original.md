```
ConversationMemory
```

A structured container for managing conversation history. It has only one field `:conversation` which is a vector of `AbstractMessage`s. It's built to support intelligent truncation and caching behavior (`get_last`).

You can also use it as a functor to have extended conversations (easier than constantly passing `conversation` kwarg)

# Examples

Basic usage

```julia
mem = ConversationMemory()
push!(mem, SystemMessage("You are a helpful assistant"))
push!(mem, UserMessage("Hello!"))
push!(mem, AIMessage("Hi there!"))

# or simply
mem = ConversationMemory(conv)
```

Check memory stats

```julia
println(mem)  # ConversationMemory(2 messages) - doesn't count system message
@show length(mem)  # 3 - counts all messages
@show last_message(mem)  # gets last message
@show last_output(mem)   # gets last content
```

Get recent messages with different options (System message, User message, ... + the most recent)

```julia
recent = get_last(mem, 5)  # get last 5 messages (including system)
recent = get_last(mem, 20, batch_size=10)  # align to batches of 10 for caching
recent = get_last(mem, 5, explain=true)    # adds truncation explanation
recent = get_last(mem, 5, verbose=true)    # prints truncation info
```

Append multiple messages at once (with deduplication to keep the memory complete)

```julia
msgs = [
    UserMessage("How are you?"),
    AIMessage("I'm good!"; run_id=1),
    UserMessage("Great!"),
    AIMessage("Indeed!"; run_id=2)
]
append!(mem, msgs)  # Will only append new messages based on run_ids etc.
```

Use for AI conversations (easier to manage conversations)

```julia
response = mem("Tell me a joke"; model="gpt4o")  # Automatically manages context
response = mem("Another one"; last=3, model="gpt4o")  # Use only last 3 messages (uses `get_last`)

# Direct generation from the memory
result = aigenerate(mem)  # Generate using full context
```
