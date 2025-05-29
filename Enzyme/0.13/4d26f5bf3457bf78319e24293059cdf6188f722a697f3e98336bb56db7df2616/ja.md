```
autodiff_deferred(::ReverseMode, f, Activity, args::Annotation...)
```

[`autodiff`](@ref) と同様ですが、GPU コードでの使用や高次微分をサポートするために遅延コンパイルを使用します。
