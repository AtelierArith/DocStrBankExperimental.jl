```
filter_events(flight::Symbol, df_event::DataFrame;
              keyword::String = "",
              tt_lim::Tuple   = ())
```

Filter a DataFrame of in-flight events to only contain relevant events.

**Arguments:**

  * `flight`:   flight name (e.g., `:Flt1001`)
  * `df_event`: lookup table (DataFrame) of in-flight events

| **Field** | **Type** | **Description**                |
|:--------- |:-------- |:------------------------------ |
| `flight`  | `Symbol` | flight name (e.g., `:Flt1001`) |
| `tt`      | `Real`   | time of `event` [s]            |
| `event`   | `String` | event description              |

  * `keyword`:  (optional) keyword to search within events, case insensitive
  * `tt_lim`:   (optional) length-`2` start & end time limits (inclusive) [s]

**Returns:**

  * `df_event`: lookup table (DataFrame) of in-flight events, filtered
