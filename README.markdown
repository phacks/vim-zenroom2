A fork of the great plugin [Zenroom2](https://github.com/amix/vim-zenroom2) with some modifications in order to make it work in terminal mode.

Here is the configuration in my `.vimrc` that plugs zenroom into Goyo:

```vimL
function! s:goyo_enter()
  silent !tmux set status off
  set noshowmode
  set noshowcmd
  set scrolloff=999
  set wrap
  set linebreak
  call zenroom2#goyo_before()
endfunction

function! s:goyo_leave()
  silent !tmux set status on
  set showmode
  set showcmd
  set scrolloff=5
  set nowrap
  set nolinebreak
  call zenroom2#goyo_after()
endfunction

autocmd! User GoyoEnter nested call <SID>goyo_enter()
autocmd! User GoyoLeave nested call <SID>goyo_leave()
```
