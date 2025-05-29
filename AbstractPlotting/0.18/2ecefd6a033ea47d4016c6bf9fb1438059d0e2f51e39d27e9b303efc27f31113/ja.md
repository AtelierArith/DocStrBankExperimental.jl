```
update_limits!(scene::Scene, limits::Union{Automatic, Rect} = scene.limits[], padding = scene.padding[])
```

この関数は、渡された `Scene` のデータに基づいて制限を更新します。テーマやその属性によって実際の制限が設定されている場合（scene.limits !== automatic）、制限は更新されません。それについては、update_limits!(scene, automatic) を呼び出してください。
