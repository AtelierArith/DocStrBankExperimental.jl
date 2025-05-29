Represents a single activity within a TCX file, encapsulating the sport type, activity ID, laps, and specific device information, as well as totals and averages for the activity.

# Fields

  * `sport`: The sport type of the activity (e.g., Biking).
  * `id`: The unique identifier for the activity, typically a timestamp.
  * `laps`: A vector of `TCXLap` representing each lap within the activity.
  * `device`: Information about the device that recorded the activity, using a `DeviceInfo` struct.
  * `total_time`: Total time for the activity.
  * `total_distance`: Total distance for the activity.
  * `max_speed`: Maximum speed achieved during the activity.
  * `total_calories`: Total calories burned during the activity.
  * `avg_hr`: Average heart rate during the activity.
  * `max_hr`: Maximum heart rate achieved during the activity.
  * `avg_cadence_zero_avg_on`: Average cadence with zero averaging ON (excluding zeros).
  * `avg_cadence_zero_avg_off`: Average cadence with zero averaging OFF (including zeros).
  * `max_cadence`: Maximum cadence achieved during the activity.
  * `avg_speed`: Average speed during the activity.
  * `total_ascent`: Total ascent during the activity.
  * `total_descent`: Total descent during the activity.
  * `max_altitude`: Maximum altitude reached during the activity.
  * `avg_watts_zero_avg_on`: Average power (watts) with zero averaging ON (excluding zeros).
  * `avg_watts_zero_avg_off`: Average power (watts) with zero averaging OFF (including zeros).
  * `max_watts`: Maximum power (watts) achieved during the activity.
