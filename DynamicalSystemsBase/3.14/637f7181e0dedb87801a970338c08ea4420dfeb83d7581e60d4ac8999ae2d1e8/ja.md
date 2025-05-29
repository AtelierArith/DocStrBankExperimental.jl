```
step!(ds::DiscreteTimeDynamicalSystem [, n::Integer]) → ds
```

離散時間ダイナミカルシステムを1ステップまたは`n`ステップ進めます。

```
step!(ds::ContinuousTimeDynamicalSystem, [, dt::Real [, stop_at_tdt]]) → ds
```

連続時間ダイナミカルシステムを1回の積分ステップ進めます。

代わりに、`dt`が指定されている場合、時間差が`≥ dt`になるまで積分を進めます（つまり、少なくとも`dt`時間進めます）。

オプションの第3引数に`true`が渡されると、積分は正確に`dt`時間進みます。
