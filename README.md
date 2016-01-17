Note for Developer mostly...

The group of Admin Scripts written in python2 and use an Apple specific python module called Foundation.
If you encounter a speed bump where the Foundation module can not be imported,
then the issue may be that you are not using default Apple python.

For example, if you happen to use pyenv to manage your python environment then
you might encounter a runtime error like this:

>sudo python check-if-virtual-machine.py
Traceback (most recent call last):
  File "check-if-virtual-machine.py", line 25, in <module>
    from Foundation import CFPreferencesCopyAppValue
ImportError: No module named Foundation

  i.e. to set the python version you are using,
then all that is needed is to point to the system install python to avoid the follow import error

>pyenv local system

This command will create/modify the python used
and create a .python-version file with contents "system" to point to the system python and the above error goes away.

Another possible solution is to change #! at the start of the script from
#!/usr/bin/env python
to use the system python
#!/usr/bin/python

Since all these python scripts are targeted for use with Apple systems,
and are dependent on the Foundation module,
the path of least resistance for me was to use pyenv switch but for more non-developer systems, this may not matter.
