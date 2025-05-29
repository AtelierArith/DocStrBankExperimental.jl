```
scorecard(values; oncompletion::Bool=false, not_completed_msg::String="", which_attempt=:completed)
```

Add a scorecard

  * `values` is a collection of pairs, `interval => message`. See below. The default summarizes the number of correct/attempted of the number of questions attempted and the total number of questions.
  * The `oncompletion` flag can be set to only show the message if all the questions have been attempted. When set, and not all questions have been attempted, the `not_completed_msg` message is shown.
  * `which_percent` is either `:correct` or `:attempted`

The interval is specified as `(l,r)`, with `0 <= l < r <= 100`, or *optionally* as `(l,r,interval_type)` where `interval_type`, a string, is one of `"[]"`, `"[)"`,`"(]"`, or `"()"`. The default interval type is `"[)"` unless `r` is `100`, in which case it is `"[]"`.

The message is shown when the percent correct/attempted is in the interval. The following values are substituted, when present:

  * `{{:total_questions}}` - the number of total questions
  * `{{:correct}}` - the number of correct answers
  * `{{:attempted}}` - the number of attempted questions
  * `{{:total_attempts}}` – the number of attempts.

The message may have Markdown formatting.

Example

```
vals = [(0,99)=>"Keep trying",
          (99, 100) => "You got {{:correct}} **correct** of {{:total_questions}} total *questions*"]
scorecard(vals)
```
