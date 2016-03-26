#The Missing (vim) Plugin Manual

A quick (work in progress) reference for using and learning popular vim plugins.

##fugitive.vim
###Git wrapper

VimCommand         | Description           | Extra Options/Instructions     |
--------------------|------------------|-----------------------|
`:GStatus`				| git status   | **+** or **-** to `add / reset -- patch`   |
`:Gread`| git checkout --filename |  Operates on the buffer rather than the filename.|
`:Gwrite`| git add |writes to both the work tree and index versions of a file, making it like git add when called from a work tree file and like git checkout when called from the index or a blob in history.
`:GCommit`|git commit||
`:GBlame`		       | git blame in vertical split   | Press enter on a line to edit the commit where the line changed, or **`o`** to open it in a split. When you're done, use **`:Gedit`** in the historic buffer to go back to the work tree version.   |
`:GMove` | git mv  | ***Simultaneously renames the buffer.***
`:GRemove` | git rm  | ***Simultaneously deletes the buffer.***
`:Gblame`| git blame| Interactive vertical split with git blame output. Press enter on a line to edit the commit where the line changed, or **`o`** to open it in a split. When you're done, use **`:Gedit`** in the historic buffer to go back to the work tree version.|
`:Gbrowse`|| Opens the current file on GitHub, with optional line range (try it in visual mode!). If your current repository isn't on GitHub, **`git instaweb`** will be spun up instead.|
`:Git`|runs any arbitrary command| **`Git!`** to open the output of a command in a temp file.|
`%{fugitive#statusline()}`| adds an indicator with the current branch in statusline. |add to **`'statusline'`** |

##Gundo
###Visual git tree browser

See also ;[Gudno configuration](http://sjl.bitbucket.org/gundo.vim/#configuration "Gundo.vim Configuration")  


VimCommand         | Description           |
--------------------|------------------|
`j` / `k` | Move up and down in graph||
`gg` / `G` | Move to top (with newest state) or bottom (oldest state)||
`:return:`|Pressing return on state or double clicking it reverts the content of the file to match that state|
`p`|make the preview window show the diff between your current state and the selected state, instead of a preview of what the selected state changed.|
'P'| will initiate "play to" mode targeted at that state. This will replay all the changes between your current state and the target, with a slight pause after each change.|
'q'|Pressing while in undo graph will close it. Also accessible by pressing mapped toggle key.|

##surround.vim
###Mappings to delete/change text surrounds (tags,brackets,quotes etc)
####Note
The instructions are a bit confusing and cumalitive and leverage off the same string. This is my best interpretation. It seems as if various character ends may be replaced in the command itself. Ex: ysiw] affects '[]' while ysiw} affects '{}', using a open bracket adds the delimiter with a space and a closing bracket does so without a space.

VimCommand         | Description | Input           | Output     |
--------------------|------------|------------------|-----------------------|
**`cs"`** | Switch double quote delimiters to single quote|**`"`** Hello world! **`"`** | **`'`** Hello world! **`'`**|
**`cs'<q>`**|Replace quote delimiters with specified tag | **`'`**Hello world!**`'`**|  **`<q>`**Hello world!**`</q>`**|
**`cst"`**|Replace tag delimiters with quotes|**`<q>`**Hello world!**`</q>`** | **`"`**Hello world!**`"`**|
**`cs{`**| Add **`{}`** ***with spaces*** to selection|||
**`cs}`**| Add **`{}`** ***without spaces*** to selection|||
**`ds"`** |Remove delimiter|**`"`**Hello world!**`"`** | Hello world!|
**`ysiw]`** | Add **`[]`** to ***selected*** text| Hello world! |**`[`**Hello**`]`** world!|
**`yssb`** or **`yss}`**|Wrap entire line in parentheses|{ Hello } world! | ({ Hello } world!)|
**`ds{ds}`**|Revert to original text| ({ Hello } world!) | Hello World!|
**`ysiw<em>`**|Emphasize hello (assuming it is selected)|Hello world!|**`<em>`**Hello**`</em>`**
**`S<p class="important">`**|Adds the specified tag with a close around the selection|**`<em>`**Hello**`</em>`** | **`<p class="important">`** `<em>`Hello`</em>` world! **`</p>`**|

##Sublime 3 Plugins
### Plugins that are helpful when using sublime

[Gitignored file excluder](https://packagecontrol.io/packages/Gitignored%20File%20Excluder) - Ignores files/folders that are listed in .gitignore during file searches. (good for ignoring .meteor/local)

[Better Coffeescript](https://packagecontrol.io/packages/Better%20CoffeeScript) - Not sure if this is really 'better' than any other Coffeescript syntax highligher but I'd like to believe so.

[Jade](https://packagecontrol.io/packages/Jade) - Jade syntax highlighting... the top plugin for the task.

[Less](https://packagecontrol.io/packages/LESS) - Top Less highlighting package.

[Monokai Extended](https://packagecontrol.io/packages/Monokai%20Extended) - This is an extended version of the popular Monokai theme; Extends Monokai from Soda with new syntax highlighting for Markdown, LESS, and Handlebars and improved syntax highlighting for RegEx, HTML, LESS, CSS, JavaScript and more. 
