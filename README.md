# vim-vsnip

This aims to plugin like Visual Studio Code's Snippet feature.


# DEMO

![vsnip-demo](https://user-images.githubusercontent.com/629908/64090812-23b7b880-cd88-11e9-96b9-9e15b8606653.gif)


# Status

Currently, No supported below features.

- variable/placeholder transform.
- nested placeholders.
- multiline changes in placeholder.

But this already useful in general case, I think.


# Setting

You should define key-mappings like below.

```
let g:vsnip_snippet_dirs = [expand('~/path/to/snippet-dir')]

imap <expr><Tab> vsnip#expandable_or_jumpable() ? '<Plug>(vsnip-expand-or-jump)' : '<Tab>'
smap <expr><Tab> vsnip#expandable_or_jumpable() ? '<Plug>(vsnip-expand-or-jump)' : '<Tab>'
nnoremap <CR> :<C-u>VsnipSelect<CR>
vnoremap <CR> :VsnipSelect<CR>
```


# FAQ

### How to define snippets?

`vim-vsnip` searches `&filetype.json` in `g:vsnip_snippet_dirs`.

When `&filetype` is `typescript.tsx`, `vim-vsnip` try to load `typescript.tsx.json`, `typescript.json` and `tsx.json`.

If found multiple snippet, those are merged.


Snippet format is same of VSCode (or Language Server Protocol).

You can find documentation in [spec](https://code.visualstudio.com/docs/editor/userdefinedsnippets.)


### How to use this with lexima?

You should define key-mapping like belwo.

```
imap <expr><Tab> vsnip#expandable_or_jumpable() ? '<Plug>(vsnip-expand-or-jump)' : lexima#expand('<LT>Tab>', 'i')
smap <expr><Tab> vsnip#expandable_or_jumpable() ? '<Plug>(vsnip-expand-or-jump)' : lexima#expand('<LT>Tab>', 'i')
```


### How to enable snippets auto-completion?

If you can use `deoplete.nvim`, use `deoplete-vsnip`.

# Known bugs

- Sometimes broken when sync same line placeholders.
  - Help wanted.
