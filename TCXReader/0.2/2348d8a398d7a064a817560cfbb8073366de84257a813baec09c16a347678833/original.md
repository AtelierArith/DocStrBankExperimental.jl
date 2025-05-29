```
calculate_averages_and_totals(lap_data::Vector{TCXLap})
```

Calculate the total values for time, distance, and calories, and average values for other metrics across all laps.

# Arguments

  * `lap_data`: A vector of `TCXLap` objects representing the laps.

# Returns

  * A tuple containing total values for time, distance, calories, ascent, descent, and average values for maximum speed, average heart rate, maximum heart rate, cadence (Zero Averaging ON and OFF), maximum cadence, average speed, max altitude, average watts (Zero Averaging ON and OFF), and max watts.
