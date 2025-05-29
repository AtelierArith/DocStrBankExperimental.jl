General callback handler for the task to report that an error occurred while running the DeviceDefender task. Error codes can only go so far in describing where/when and how the failure occur so the errors here may best communicate where/when and the how of the underlying call should be found in log output

# Arguments

  * `is_task_stopped`:[in] flag indicating whether or not the task is unable to continue running
  * `error_code`:[in] error code describing the nature of the failure
