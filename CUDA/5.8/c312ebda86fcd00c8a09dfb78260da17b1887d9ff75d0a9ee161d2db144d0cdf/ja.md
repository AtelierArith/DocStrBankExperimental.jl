```
threadfence_block()
```

メモリフェンスであり、次のことを保証します：

  * `threadfence_block()`の呼び出し前に呼び出しスレッドによって行われたすべてのメモリへの書き込みは、呼び出しスレッドのブロック内のすべてのスレッドによって、`threadfence_block()`の呼び出し後に呼び出しスレッドによって行われたすべてのメモリへの書き込みの前に発生したものとして観察されます。
  * `threadfence_block()`の呼び出し前に呼び出しスレッドによって行われたすべてのメモリからの読み取りは、`threadfence_block()`の呼び出し後に呼び出しスレッドによって行われたすべてのメモリからの読み取りの前に順序付けられます。
