```
calc_orient_rot(x, y, z; viewer=false, ENU=true)
```

カイト参照フレームに基づいて回転行列を計算します。デフォルトではENU（東、北、上）として渡されますが、ENUがfalseの場合はNED（北、東、下）として渡されます。viewerがtrueの場合、回転行列はビューワー参照フレームに関して計算されます。
