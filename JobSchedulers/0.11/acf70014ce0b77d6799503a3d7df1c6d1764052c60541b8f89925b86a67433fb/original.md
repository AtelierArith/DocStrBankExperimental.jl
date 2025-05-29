```
Cron(second, minute, hour, day_of_month, month, day_of_week)
Cron(;
    second = 0,
    minute = '*',
    hour = '*',
    day_of_month = '*',
    month = '*',
    day_of_week = '*',
)
```

`Cron` stores the schedule of a repeative `Job`, implemented according to Linux-based `crontab`(5) table.

Jobs are executed when the **second, minute, hour and month** fields match the current time. If neither `day_of_month` nor `day_of_week` **starts with** `*`, cron takes the union (∪) of their values `day_of_month ∪ day_of_week`. Otherwise cron takes the intersection (∩) of their values `day_of_month ∩ day_of_week`.

## When an argument is an `Int`:

|          Field |    Allowed values |
| --------------:| -----------------:|
|       `second` |              0-59 |
|       `minute` |              0-59 |
|         `hour` |              0-23 |
| `day_of_month` |              1-31 |
|        `month` |              1-12 |
|  `day_of_week` | 1-7 (1 is Monday) |

!!! compat "Diff between Linux crontab"
    1. Typical Linux distributions do not have `second` filed as JobSchedulers.
    2. Sunday is only coded `7` in JobSchedulers, while it is `0` or `7` in Linux, so the behaviors like `day_of_week = "*/2"` are different in two systems.
    3. From JobSchedulers v0.11, `Cron` has been rewritten based on the standard crontab, including its bug described [here](https://crontab.guru/cron-bug.html).


## When an argument is a `String` or `Char`:

An argument may be an asterisk (`*`), which always stands for $first-last$.

Ranges of numbers are allowed. Ranges are two numbers separated with a hyphen. The specified range is inclusive. For example, 8-11 for an $hours$ entry specifies execution at hours 8, 9, 10 and 11.

Lists are allowed. A list is a set of numbers (or ranges) separated by commas. Examples: `"1,2,5,9"`, `"0-4,8-12"`.

Step values can be used in conjunction with ranges. Following a range with `/<number>` specifies skips of the number's value through the range. For example, `"0-23/2"` can be used in the `hour` argument to specify Job execution every other hour (the alternative is `"0,2,4,6,8,10,12,14,16,18,20,22"`). Steps are also permitted after an asterisk, so if you want to say $every two hours$, just use `"*/2"`.

## When an argument is a `Vector`:

`Vector` works like lists mentioned above. For example, `[1,2,5,9]` is equivalent to `"1,2,5,9"`.

## When an argument is a `UInt64`:

`UInt64` is the internal type of `Cron` fileds. All the previous types will be converted to a `UInt64` bit array. The start index of the bit array is 0. Bits outside of the allowed values (see the table above) are ignored.
