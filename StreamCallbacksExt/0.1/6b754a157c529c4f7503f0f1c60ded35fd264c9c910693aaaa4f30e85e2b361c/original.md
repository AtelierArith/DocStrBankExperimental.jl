```
TokenCounts(; input=0, output=0, cache_write=0, cache_read=0)
```

Tracks token usage across different categories:

  * `input`: Number of new tokens in prompt (excluding cached tokens)
  * `output`: Number of generated tokens in response
  * `cache_write`: Number of tokens written to cache
  * `cache_read`: Number of tokens read from cache

Note: Total input tokens = input + cache*write + cache*read
