```
tobday(calendar, dt; [forward=true]) :: Dates.Date
```

Adjusts `dt` to next Business Day if it's not a Business Day. If `isbday(dt)`, returns `dt`.
