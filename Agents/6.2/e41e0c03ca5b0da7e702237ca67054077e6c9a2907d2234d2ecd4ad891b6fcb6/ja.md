```
add_event!(agent, model)
```

`agent`のためにランダムに選ばれたイベントを生成し、`EventQueueABM`に記載されているように、傾向に基づいてキューに追加します。

```
add_event!(agent, event_idx, t::Real, model::EventQueueABM)
```

`model`に与えられた`events`からのイベントのインデックスに基づいて、`agent`のためにトリガーされる新しいイベントをキューに追加します。このイベントは、`model`の現在の時間から`t`時間後にトリガーされます。
