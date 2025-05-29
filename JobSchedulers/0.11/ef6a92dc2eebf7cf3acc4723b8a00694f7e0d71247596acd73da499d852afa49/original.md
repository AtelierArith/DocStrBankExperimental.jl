```
Cron(special::Symbol)
```

Instead of the six arguments of `Cron`, one of the following special symbols may appear instead:

|   `special` |                                       Meaning |
| -----------:| ---------------------------------------------:|
|   `:yearly` |          Run once a year, `Cron(0,0,0,1,1,0)` |
| `:annually` |                           (same as `:yearly`) |
|  `:monthly` |     Run once a month, `Cron(0,0,0,1,'*','*')` |
|   `:weekly` |      Run once a week, `Cron(0,0,0,'*','*',1)` |
|    `:daily` |     Run once a day, `Cron(0,0,0,'*','*','*')` |
| `:midnight` |                            (same as `:daily`) |
|   `:hourly` | Run once an hour, `Cron(0,0,'*','*','*','*')` |
|     `:none` |             Never repeat, `Cron(0,0,0,0,0,0)` |

Caution: Linux crontab's special `:reboot` is not supported here.

To run every minute, just use `Cron()`.
