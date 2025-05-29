`bodev(sys::LTISystem, w::AbstractVector; $(Expr(:kw, :unwrap, true)))`

SISOシステムで使用するためのもので、返される値の余分な次元が削除されるため、`bode`と同様に動作します。
