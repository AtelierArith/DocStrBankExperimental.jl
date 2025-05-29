price_history(ticker, freq, start::DateTime=now()-Day(1), stop::DateTime=now())

get the price history with `interval` ticks from `start` to `stop`

valid frequency: minute: 1*, 5, 10, 15, 30
