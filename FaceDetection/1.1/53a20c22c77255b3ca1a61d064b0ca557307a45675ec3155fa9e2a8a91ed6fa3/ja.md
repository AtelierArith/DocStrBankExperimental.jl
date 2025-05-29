```
mutable struct HaarLikeObject{I <: Integer, F <: AbstractFloat}

    Haar-like特徴を表す構造体。
    
feature_type::Tuple{I, I}
position::Tuple{I, I}
top_left::Tuple{I, I}
bottom_right::Tuple{I, I}
width::I
height::I
threshold::I
polarity::I
weight::F
```
