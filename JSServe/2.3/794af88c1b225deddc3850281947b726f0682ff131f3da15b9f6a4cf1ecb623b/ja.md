```
onjs(session::Session, obs::Observable, func::JSCode)
```

`session`にjavascript関数を登録し、`obs`が新しい値を取得したときに呼び出されます。observableがJS側から更新されると、`func`の呼び出しは完全にjavascript内でトリガーされ、Julia `session`との通信は行われません。
