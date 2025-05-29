```
transform_window(; [frame], [ignorePeers], [groupby],[ sortby], operations...)
```

Creates a `TransformSpec` for the given window operations. If a sortby field starts with '-' then descending order is used. See more in Vega-Lite's [documentation](https://vega.github.io/vega-lite/docs/window.html)
