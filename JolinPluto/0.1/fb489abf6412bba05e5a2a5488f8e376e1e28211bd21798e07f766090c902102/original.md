```
repeat_at(t -> (rand(), t), ceil(now(), Second(10)), init=:wait)

repeat_at(ceil(now(), Second(10)), init=:wait) do t
	# code to be returned repeatedly
	rand(), t
end
```

When run inside Pluto it will rerun the function on the next specified time, again and again.

## Keyword Arguments

  * `init` specifies what to do at first run or re-evaluation caused by standard reactivity. You can specify any function (e.g. `init=myinit_func`)or one of the two special values `:wait` und `:run`. `:wait` (default) will wait for the next time and then run the code. `:run` will run the code immediately without waiting.
