```
on_ready(agent::Agent)
```

エージェントシステム全体が準備完了したときに呼び出されるライフサイクルフックイン関数で、フックインはnotify_ready(container::Container)を使用して手動でアクティブ化する必要があります。`activate`関数を使用すると、自動的に呼び出されます。
