Calculates volume bars with a constant volume per bar.  Input is a dataframe in the following order: Time, Price, Volume

Output is a dataframe in the following order: Time, Open, High, Low, Close, Volume

# Keyword arguments

  * `method` : chooses the mode used to generate volume bars, "constant" is set by default and "SMA", "EMA" will be implemented later on.
  * `threshold` : threshold for the volume accumulator, a new candle will be produced when the cumulative volume exceeds this number.
  * `frequency` : not used
  * `windowlen` : not used
