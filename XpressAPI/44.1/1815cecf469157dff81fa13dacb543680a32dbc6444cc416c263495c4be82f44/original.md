```
XPRSaddcbgapnotify(prob, cb, priority)
```

# Arguments

  * `cbprob`: The current problem.
  * `relgapnotifytarget`: The value the MIPRELGAPNOTIFY control will be set to after this callback. May be modified within the callback in order to set a new notification target.
  * `absgapnotifytarget`: The value the MIPABSGAPNOTIFY control will be set to after this callback. May be modified within the callback in order to set a new notification target.
  * `absgapnotifyobjtarget`: The value the MIPABSGAPNOTIFYOBJ control will be set to after this callback. May be modified within the callback in order to set a new notification target.
  * `absgapnotifyboundtarget`: The value the MIPABSGAPNOTIFYBOUND control will be set to after this callback. May be modified within the callback in order to set a new notification target.

`cb` will be invoked with this signature:

```
cb(cbprob, relgapnotifytarget, absgapnotifytarget, absgapnotifyobjtarget, absgapnotifyboundtarget)::relgapnotifytarget, absgapnotifytarget, absgapnotifyobjtarget, absgapnotifyboundtarget
```
