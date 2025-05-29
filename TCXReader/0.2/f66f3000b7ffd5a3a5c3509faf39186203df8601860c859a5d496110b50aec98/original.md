Represents a single lap within a TCX file, encapsulating temporal, physiological, and spatial metrics through track points, along with an optional average speed obtained from extensions.

# Parameters

  * `startTime`: The lap's start time.
  * `totalTimeSeconds`: Total time in seconds.
  * `distanceMeters`: Distance in meters.
  * `maximumSpeed`: Maximum speed in m/s, optional.
  * `calories`: Calories burned.
  * `averageHeartRateBpm`: Average heart rate in BPM, optional.
  * `maximumHeartRateBpm`: Maximum heart rate in BPM, optional.
  * `intensity`: Lap intensity.
  * `cadence`: Cadence, optional.
  * `trackPoints`: Track points vector.
  * `triggerMethod`: Trigger method for the lap.
  * `avgSpeed`: Average speed in m/s from `<ns3:AvgSpeed>` extension, optional.
