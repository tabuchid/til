# Run only one instance of mvim ie client-server mode

Put the following into your `.bashrc` or `.zshrc`

```
function mvim {
  if [ -n "$1" ] ; then
    command mvim --remote-silent "$@"
  elif [ -n "$( command mvim --serverlist )" ] ; then
    command mvim --remote-send ":call foreground()<CR>:enew<CR>:<BS>"
  else
    command mvim
  fi
}
```
