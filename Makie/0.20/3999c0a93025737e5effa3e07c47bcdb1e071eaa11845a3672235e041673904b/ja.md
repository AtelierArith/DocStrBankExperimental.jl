```
set_close_to!(slider, value) -> closest_value
```

スライダーを `value` に最も近いスライダーの範囲内の値に設定し、この値を返します。この関数は、スライダーの値のオブザーバブルを直接変更するのではなく、プログラム的にスライダーを値に設定するために使用する必要があります。直接変更すると、スライダーが視覚的に更新されません。
