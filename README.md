# 萌娘百科歌词提取助手

一键提取[萌娘百科](https://zh.moegirl.org.cn)中使用 `{{LyricsKai}}` 模板显示的歌词，将原文和译文分开呈现在文本框中，可一键复制。

## 项目背景

我在进行动漫相关话题的写作讨论时，有时会需要从萌百上引用一些动漫音乐的歌词，但是萌百的歌词出现原文和译文对照的时候使用的 `{{LyricsKai}}` 模板并不方便将原文和译文分开复制。如果直接复制，得到的结果是一行原文一行译文夹杂在一起，中间带空行，最后还会出现一段萌百添加的附加内容；但是引用歌词的时候，我希望把原文和译文分开，先单独复制原文，再单独复制译文，中间不带空行，也不带最后的附加内容。于是我就写了这么一个简单的小脚本。

> 查看页面源代码虽然在某些情况下也可以实现复制歌词内容的目的，但是日文歌词上面常常会利用 `{{Photrans}}` 模板标注振假名，此时直接复制页面源代码中的歌词会把这一堆 `{{Photrans}}` 模板也给复制下来，很不方便，所以这么一个工具还是有必要的。

## 脚本的添加和运行

你可以通过复制脚本全文，在 TamperMonkey 中新建用户脚本然后粘贴的方法来添加此脚本。

脚本运行后，“歌词提取助手”的选项会被添加到萌娘百科的菜单栏中。此操作在 Vector 皮肤和 MoeSkin 皮肤下的运行结果略有差异——

* 若使用 Vector 皮肤，菜单栏是在页面左侧，脚本运行后，“歌词提取助手”会被添加到“工具”子栏目下。同时为了方便操作，脚本会将“工具”子栏目从原来的最下方移动到第二个子栏目的位置。
* 若使用 MoeSkin 皮肤，菜单栏在页面右下方固定位置，“歌词提取助手”会被添加到最后一项。

## 使用方法

首先进入你想要提取歌词的条目，然后点击“歌词提取助手”，就会弹出一个对话框。对话框里包含每一段歌词的原文和译文，点击歌词框右上角的“复制”按钮即可一键复制歌词全文。当然你也可以直接在文本框中选中自己需要的歌词段落来复制。

如果有多段歌词，则可以通过滚动整个对话框页面的方式来向上或向下翻页，访问其他段歌词。

## 已知问题

* 在处理使用 `{{Utawari}}` 模板创建的歌词时，输出结果可能会包含不必要的空行。
* 对话框弹出时，页面锁定滚动我还没有找到合适的方法能保证页面不会自动滑回顶端且内容不发生偏移。我目前使用的办法是记录下滚动的位置，对话框弹出时使用 CSS 属性 `transform` 对整个文档向上平移，将文档的 `overflow` 属性设为 `hidden`，关闭后再恢复 `overflow` 属性、取消平移，但是这样带来的问题是对话框弹出后页面会有明显的闪动且背景图发生错位。


