```
autodiff_deferred(::ForwardMode, f, Activity, args::Annotation...)
```

`autodiff(::ForwardMode, f, Activity, args...)` と同様ですが、GPU コードでの使用や高次微分をサポートするために遅延コンパイルを使用します。
