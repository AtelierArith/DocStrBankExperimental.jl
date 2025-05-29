```
BerryCurvature{B<:ReciprocalSpace, M<:BerryCurvatureMethod} <: Action
```

エネルギーバンドのベリー曲率。

!!! note
    回転対称なベリー曲率を得るためには、`:rcoordinate`ゲージを使用する必要があります。そうしないと、人工的なわずかな回転対称性の破れが発生します。

