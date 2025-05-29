```
aws_iotdevice_defender_task_clean_up(defender_task)
```

Cancels the running task reporting Device Defender metrics and cleans up. If the task is currently running, it will block until the task has been canceled and cleaned up successfully

# Arguments

  * `defender_task`:[in] running task to stop and clean up

### Prototype

```c
void aws_iotdevice_defender_task_clean_up(struct aws_iotdevice_defender_task *defender_task);
```
