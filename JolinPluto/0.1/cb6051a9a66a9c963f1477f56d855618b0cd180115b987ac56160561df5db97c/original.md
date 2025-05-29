```
@repeat_at(ceil(now(), Second(10)), init=:wait) do t
	# code to be returned repeatedly
	rand(), t
end

@repeat_at(ceil(now(), Second(10)), init=:wait)
```

When run inside Pluto it will rerun the function on the next specified time, again and again.

## Keyword Arguments

  * `init` specifies what to do at first run or re-evaluation caused by standard reactivity. You can specify any code or function call (e.g. `init=nothing`, or `init=myinit()`). In addition there are two special values `:wait` und `:run`. `:wait` (default) will wait for the next time and then run the code. `:run` will run the code immediately without waiting.
