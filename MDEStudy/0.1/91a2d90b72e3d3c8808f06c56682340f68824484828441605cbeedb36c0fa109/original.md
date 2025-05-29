```
MarketCalendar
* `bdays`: a vector of business days
* `dtmin`: minimum date allowed to check for bdays in bdays set. Defaults to `min(bdays...)`.
* `dtmax`: maximum date allowed to check for bdays in bdays set. Defaults to `max(bdays...)`.
* `isbday_array`: a boolean vector mapping a period days from market data.
* `bdayscounter_array`: a cumulative sum of business days.
```
