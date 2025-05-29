```
Nearest(f::Function, handle::Message)
```

メッセージからNearestを作成し、完了時に自動的に破棄します。

# 例

```Julia
Nearest(handle) do near
    find(near, handle, inlat, inlon)
end
```
