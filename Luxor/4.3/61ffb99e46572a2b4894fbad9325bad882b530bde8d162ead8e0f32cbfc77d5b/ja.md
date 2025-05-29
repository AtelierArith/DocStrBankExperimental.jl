```
ngonside(centerpoint::Point, sidelength::Real, sides::Int=5, orientation=0;
        action=:none,
        vertices=false,
        reversepath=false)
ngonside(centerpoint::Point, sidelength::Real, sides::Int, orientation, action;
        vertices=false,
        reversepath=false)
```

`centerpoint`を中心とし、`sides`の辺を持つ、辺の長さが`sidelength`の正多角形を描画します。
