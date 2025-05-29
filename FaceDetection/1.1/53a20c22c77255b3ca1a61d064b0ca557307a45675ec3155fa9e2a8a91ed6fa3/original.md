```
mutable struct HaarLikeObject{I <: Integer, F <: AbstractFloat}

    Struct representing a Haar-like feature.
    
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
