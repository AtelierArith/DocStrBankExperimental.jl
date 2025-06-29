```
plot_historical_vol(pair::String, interval::Int64 = 300)
```

Plot historical volume data in the REPL.

# Arguments

  * `pair::String` : Specify currency pair, for example "ETH-EUR"
  * `interval::Int64` : Rates are returned in grouped buckets based on specified interval.                     Choose one from [60, 300 (default), 900, 3600, 21600, 86400], all in seconds.

# Example

```julia-repl
julia> plot_historical_vol("ETH-EUR", 21600)
                               ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀Volume for ETH-EUR in intervals of 21600 seconds⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀ 
                               ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓ 
                         6 000 ┃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡆⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀┃ 
                               ┃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀┃ 
                               ┃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀┃ 
                               ┃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡇⠀⠀⠀⠀⠀⠀⠀⡇⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀┃ 
                               ┃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡇⠀⠀⠀⠀⠀⠀⡆⡇⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀┃ 
                               ┃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡇⠀⠀⠀⠀⠀⠀⣷⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀┃ 
                               ┃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣸⡇⡀⠀⠀⠀⡀⠀⣿⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀┃ 
   Number of coins [ETH]       ┃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⡇⡇⠀⠀⠀⡇⡀⣿⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀┃ 
                               ┃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⢸⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⢀⣿⡇⡇⠀⠀⠀⣷⡇⣿⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀┃ 
                               ┃⠀⡇⠀⠀⠀⠀⠀⡀⡄⠀⠀⠀⢸⣸⡇⠀⡄⠀⠀⠀⡆⠀⠀⠀⠀⠀⠀⠀⠀⠀⣿⠀⠀⠀⠀⠀⡆⠀⡇⠀⠀⢸⣿⣇⢿⠀⠀⠀⣿⣷⠉⣿⢇⠀⣦⠀⠀⠀⡇⠀⠀⠀⡆⡇⠀⡀⡄⠀⠀⠀⠀⠀⠀⠀⠀┃ 
                               ┃⣠⡇⢠⡆⠀⠀⢰⣿⡇⢸⡇⡆⢸⣿⡇⢰⣇⡆⠀⢰⡇⠀⡆⠀⠀⠀⠀⠀⡆⣠⣿⡇⠀⠀⠀⢀⡇⢰⡇⠀⠀⢸⢸⣿⠘⡄⠀⢸⢿⠇⠀⢻⢸⠀⣿⠀⠀⠀⣷⡀⠀⢀⢷⣇⠀⡇⡇⠀⠀⠀⡇⠀⠀⠀⠀┃ 
                               ┃⣿⣧⣼⡇⠀⢀⣸⣿⣇⣸⡇⡇⡜⣿⣷⣿⣿⡇⠀⣼⣧⣧⣷⡀⠀⠀⢀⢰⣧⣿⣿⡇⠀⠀⠀⢸⢣⣿⡇⠀⠀⡜⠀⢿⠀⡇⠀⢸⢸⠀⠀⢸⢸⠀⣿⡄⡇⣧⢻⡇⠀⢸⢸⢻⡇⣇⡇⠀⠀⡆⡇⣷⡆⠀⠀┃ 
                               ┃⣿⣿⣿⡇⢠⣾⣿⣿⣿⡏⡇⣧⠃⣿⢻⣿⣿⣿⡄⡇⢹⢹⣿⣧⡄⠀⢸⣾⣿⣿⢹⡇⣠⠀⢠⣾⠘⣿⡇⠀⠀⡇⠀⢸⠀⡇⠀⡎⠈⠀⠀⠈⢸⣆⡏⣿⢱⢻⢸⡇⠀⢸⢸⢸⢧⣿⢱⠀⠀⡇⣿⣿⢇⡇⠀┃ 
                               ┃⢿⢿⣿⣇⣼⣿⢿⣿⢿⠁⣧⢿⠀⠘⠘⣿⠸⢿⣧⡇⠀⠀⢸⠛⢧⣧⠾⠈⣿⢹⠘⢣⡟⢦⠃⣿⠀⠁⢣⢾⢻⠃⠀⠈⠀⢷⣤⠃⠀⠀⠀⠀⠘⠸⠀⠸⢸⠸⢸⢣⡀⡸⢸⠈⢸⢸⠸⢤⢿⢸⢻⠸⢸⡇⠀┃ 
                             0 ┃⠀⠀⠛⠙⠉⠈⠀⠘⠀⠀⠻⠈⠀⠀⠀⠙⠀⠈⠙⠀⠀⠀⠈⠀⠈⠃⠀⠀⠘⠀⠀⠈⠀⠈⠀⠈⠀⠀⠘⠈⠈⠀⠀⠀⠀⠘⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠸⠱⠁⠈⠀⠈⠘⠀⠀⠈⠈⠀⠀⠈⠘⠳┃ 
                               ┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛ 
                               ⠀2023-11-21T12:00:00⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀2024-02-04T06:00:00⠀ 
                               ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀Time⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀ 
```
