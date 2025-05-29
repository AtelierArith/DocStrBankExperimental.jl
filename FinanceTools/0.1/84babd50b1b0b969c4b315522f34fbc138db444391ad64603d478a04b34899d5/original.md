Calculates dollar bars with a constant amount of dollars per bar.  Input is a dataframe in the following order: Time, Price, Volume

Output is a dataframe in the following order: Time, Open, High, Low, Close, Volume

# Keyword arguments

  * `method` : chooses the mode used to generate dollar bars, "constant" is set by default and "SMA", "EMA" will be implemented later on.
  * `threshold` : threshold for the dollar accumulator, a new candle will be produced when the cumulative dollar amount exceeds this number.
  * `frequency` : not used
  * `windowlen` : not used
