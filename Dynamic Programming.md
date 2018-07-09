<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Dynamic Programming</title>
    <style>body { padding: 0; margin: 0; }
.markdown-preview-plus-view:not([data-use-github-style]) {
  padding: 2em;
  font-size: 1.2em;
  color: #555;
  background-color: white;
}
.markdown-preview-plus-view:not([data-use-github-style]) span.critic.comment > span {
  background-color: white;
}
.markdown-preview-plus-view:not([data-use-github-style]) > :first-child {
  margin-top: 0;
}
.markdown-preview-plus-view:not([data-use-github-style]) h1,
.markdown-preview-plus-view:not([data-use-github-style]) h2,
.markdown-preview-plus-view:not([data-use-github-style]) h3,
.markdown-preview-plus-view:not([data-use-github-style]) h4,
.markdown-preview-plus-view:not([data-use-github-style]) h5,
.markdown-preview-plus-view:not([data-use-github-style]) h6 {
  line-height: 1.2;
  margin-top: 1.5em;
  margin-bottom: 0.5em;
  color: #030303;
}
.markdown-preview-plus-view:not([data-use-github-style]) h1 {
  font-size: 2.4em;
  font-weight: 300;
}
.markdown-preview-plus-view:not([data-use-github-style]) h2 {
  font-size: 1.8em;
  font-weight: 400;
}
.markdown-preview-plus-view:not([data-use-github-style]) h3 {
  font-size: 1.5em;
  font-weight: 500;
}
.markdown-preview-plus-view:not([data-use-github-style]) h4 {
  font-size: 1.2em;
  font-weight: 600;
}
.markdown-preview-plus-view:not([data-use-github-style]) h5 {
  font-size: 1.1em;
  font-weight: 600;
}
.markdown-preview-plus-view:not([data-use-github-style]) h6 {
  font-size: 1em;
  font-weight: 600;
}
.markdown-preview-plus-view:not([data-use-github-style]) strong {
  color: #030303;
}
.markdown-preview-plus-view:not([data-use-github-style]) del {
  color: #7e7e7e;
}
.markdown-preview-plus-view:not([data-use-github-style]) a,
.markdown-preview-plus-view:not([data-use-github-style]) a code {
  color: black;
}
.markdown-preview-plus-view:not([data-use-github-style]) img {
  max-width: 100%;
}
.markdown-preview-plus-view:not([data-use-github-style]) > p {
  margin-top: 0;
  margin-bottom: 1.5em;
}
.markdown-preview-plus-view:not([data-use-github-style]) > ul,
.markdown-preview-plus-view:not([data-use-github-style]) > ol {
  margin-bottom: 1.5em;
}
.markdown-preview-plus-view:not([data-use-github-style]) blockquote {
  margin: 1.5em 0;
  font-size: inherit;
  color: #7e7e7e;
  border-color: #d6d6d6;
  border-width: 4px;
}
.markdown-preview-plus-view:not([data-use-github-style]) hr {
  margin: 3em 0;
  border-top: 2px dashed #d6d6d6;
  background: none;
}
.markdown-preview-plus-view:not([data-use-github-style]) table {
  margin: 1.5em 0;
}
.markdown-preview-plus-view:not([data-use-github-style]) th {
  color: #030303;
}
.markdown-preview-plus-view:not([data-use-github-style]) th,
.markdown-preview-plus-view:not([data-use-github-style]) td {
  padding: 0.66em 1em;
  border: 1px solid #d6d6d6;
}
.markdown-preview-plus-view:not([data-use-github-style]) pre,
.markdown-preview-plus-view:not([data-use-github-style]) code {
  color: #030303;
  background-color: #f0f0f0;
}
.markdown-preview-plus-view:not([data-use-github-style]) pre,
.markdown-preview-plus-view:not([data-use-github-style]) pre.editor-colors {
  margin: 1.5em 0;
  padding: 1em;
  font-size: 0.92em;
  border-radius: 3px;
  background-color: #f5f5f5;
}
.markdown-preview-plus-view:not([data-use-github-style]) kbd {
  color: #030303;
  border: 1px solid #d6d6d6;
  border-bottom: 2px solid #c7c7c7;
  background-color: #f0f0f0;
}

@include 'style-variables';
.markdown-preview-plus-view {
  display: block;
  overflow-x: hidden;
}
.markdown-preview-plus-view .emoji {
  max-width: 1em !important;
}
.markdown-preview-plus-view del {
  text-decoration: none;
  position: relative;
}
.markdown-preview-plus-view del::after {
  border-bottom: 1px solid black;
  content: '';
  left: 0;
  position: absolute;
  right: 0;
  top: 50%;
}
.markdown-preview-plus-view .flash {
  -webkit-animation: flash 1s ease-out;
  -webkit-animation-iteration-count: 1;
  outline: 1px solid rgba(255, 0, 0, 0);
}
@-webkit-keyframes flash {
  0% {
    outline-color: rgba(255, 0, 0, 0);
  }
  50% {
    outline-color: #ff0000;
  }
  100% {
    outline-color: rgba(255, 0, 0, 0);
  }
}
.markdown-preview-plus-view pre.editor-colors {
  display: block;
  overflow: auto;
  white-space: pre-line;
}
.markdown-preview-plus-view pre.editor-colors .line {
  display: inline;
}
@media print {
  .markdown-preview-plus-view pre.editor-colors {
    overflow: visible !important;
  }
  .markdown-preview-plus-view pre.editor-colors .line {
    white-space: pre-wrap !important;
  }
}
.markdown-preview-plus-view ul.contains-task-list li.task-list-item {
  position: relative;
  list-style-type: none;
}
.markdown-preview-plus-view ul.contains-task-list li.task-list-item input.task-list-item-checkbox {
  position: absolute;
  transform: translateX(-100%);
  width: 30px;
}
.markdown-preview-plus-view span.critic.comment {
  position: relative;
}
.markdown-preview-plus-view span.critic.comment::before {
  content: '\1f4ac';
  position: initial;
}
.markdown-preview-plus-view span.critic.comment > span {
  display: none;
}
.markdown-preview-plus-view span.critic.comment:hover > span {
  display: initial;
  position: absolute;
  top: 100%;
  left: 0;
  border: 1px solid;
  border-radius: 5px;
  max-height: 4em;
  overflow: auto;
}
.markdown-preview-plus-view span.critic.comment:focus > span {
  display: initial;
  text-decoration: underline;
  position: initial;
  top: auto;
  left: auto;
  border: initial;
  border-radius: initial;
}

body.markdown-preview-plus-view[data-use-github-style] {
  overflow: initial !important;
}
.markdown-preview-plus-view[data-use-github-style] {
  overflow: hidden;
  font-family: "Helvetica Neue", Helvetica, "Segoe UI", Arial, freesans, sans-serif;
  line-height: 1.6;
  word-wrap: break-word;
  padding: 30px;
  font-size: 16px;
  color: #333;
  background-color: #fff;
}
.markdown-preview-plus-view[data-use-github-style] > *:first-child {
  margin-top: 0 !important;
}
.markdown-preview-plus-view[data-use-github-style] > *:last-child {
  margin-bottom: 0 !important;
}
.markdown-preview-plus-view[data-use-github-style] a:not([href]) {
  color: inherit;
  text-decoration: none;
}
.markdown-preview-plus-view[data-use-github-style] .absent {
  color: #c00;
}
.markdown-preview-plus-view[data-use-github-style] .anchor {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  padding-right: 6px;
  padding-left: 30px;
  margin-left: -30px;
}
.markdown-preview-plus-view[data-use-github-style] .anchor:focus {
  outline: none;
}
.markdown-preview-plus-view[data-use-github-style] h1,
.markdown-preview-plus-view[data-use-github-style] h2,
.markdown-preview-plus-view[data-use-github-style] h3,
.markdown-preview-plus-view[data-use-github-style] h4,
.markdown-preview-plus-view[data-use-github-style] h5,
.markdown-preview-plus-view[data-use-github-style] h6 {
  position: relative;
  margin-top: 1em;
  margin-bottom: 16px;
  font-weight: bold;
  line-height: 1.4;
}
.markdown-preview-plus-view[data-use-github-style] h1 .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h2 .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h3 .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h4 .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h5 .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h6 .octicon-link {
  display: none;
  color: #000;
  vertical-align: middle;
}
.markdown-preview-plus-view[data-use-github-style] h1:hover .anchor,
.markdown-preview-plus-view[data-use-github-style] h2:hover .anchor,
.markdown-preview-plus-view[data-use-github-style] h3:hover .anchor,
.markdown-preview-plus-view[data-use-github-style] h4:hover .anchor,
.markdown-preview-plus-view[data-use-github-style] h5:hover .anchor,
.markdown-preview-plus-view[data-use-github-style] h6:hover .anchor {
  padding-left: 8px;
  margin-left: -30px;
  text-decoration: none;
}
.markdown-preview-plus-view[data-use-github-style] h1:hover .anchor .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h2:hover .anchor .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h3:hover .anchor .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h4:hover .anchor .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h5:hover .anchor .octicon-link,
.markdown-preview-plus-view[data-use-github-style] h6:hover .anchor .octicon-link {
  display: inline-block;
}
.markdown-preview-plus-view[data-use-github-style] h1 tt,
.markdown-preview-plus-view[data-use-github-style] h2 tt,
.markdown-preview-plus-view[data-use-github-style] h3 tt,
.markdown-preview-plus-view[data-use-github-style] h4 tt,
.markdown-preview-plus-view[data-use-github-style] h5 tt,
.markdown-preview-plus-view[data-use-github-style] h6 tt,
.markdown-preview-plus-view[data-use-github-style] h1 code,
.markdown-preview-plus-view[data-use-github-style] h2 code,
.markdown-preview-plus-view[data-use-github-style] h3 code,
.markdown-preview-plus-view[data-use-github-style] h4 code,
.markdown-preview-plus-view[data-use-github-style] h5 code,
.markdown-preview-plus-view[data-use-github-style] h6 code {
  font-size: inherit;
}
.markdown-preview-plus-view[data-use-github-style] h1 {
  padding-bottom: 0.3em;
  font-size: 2.25em;
  line-height: 1.2;
  border-bottom: 1px solid #eee;
}
.markdown-preview-plus-view[data-use-github-style] h1 .anchor {
  line-height: 1;
}
.markdown-preview-plus-view[data-use-github-style] h2 {
  padding-bottom: 0.3em;
  font-size: 1.75em;
  line-height: 1.225;
  border-bottom: 1px solid #eee;
}
.markdown-preview-plus-view[data-use-github-style] h2 .anchor {
  line-height: 1;
}
.markdown-preview-plus-view[data-use-github-style] h3 {
  font-size: 1.5em;
  line-height: 1.43;
}
.markdown-preview-plus-view[data-use-github-style] h3 .anchor {
  line-height: 1.2;
}
.markdown-preview-plus-view[data-use-github-style] h4 {
  font-size: 1.25em;
}
.markdown-preview-plus-view[data-use-github-style] h4 .anchor {
  line-height: 1.2;
}
.markdown-preview-plus-view[data-use-github-style] h5 {
  font-size: 1em;
}
.markdown-preview-plus-view[data-use-github-style] h5 .anchor {
  line-height: 1.1;
}
.markdown-preview-plus-view[data-use-github-style] h6 {
  font-size: 1em;
  color: #777;
}
.markdown-preview-plus-view[data-use-github-style] h6 .anchor {
  line-height: 1.1;
}
.markdown-preview-plus-view[data-use-github-style] p,
.markdown-preview-plus-view[data-use-github-style] blockquote,
.markdown-preview-plus-view[data-use-github-style] ul,
.markdown-preview-plus-view[data-use-github-style] ol,
.markdown-preview-plus-view[data-use-github-style] dl,
.markdown-preview-plus-view[data-use-github-style] table,
.markdown-preview-plus-view[data-use-github-style] pre {
  margin-top: 0;
  margin-bottom: 16px;
}
.markdown-preview-plus-view[data-use-github-style] hr {
  height: 4px;
  padding: 0;
  margin: 16px 0;
  background-color: #e7e7e7;
  border: 0 none;
}
.markdown-preview-plus-view[data-use-github-style] ul,
.markdown-preview-plus-view[data-use-github-style] ol {
  padding-left: 2em;
}
.markdown-preview-plus-view[data-use-github-style] ul.no-list,
.markdown-preview-plus-view[data-use-github-style] ol.no-list {
  padding: 0;
  list-style-type: none;
}
.markdown-preview-plus-view[data-use-github-style] ul ul,
.markdown-preview-plus-view[data-use-github-style] ul ol,
.markdown-preview-plus-view[data-use-github-style] ol ol,
.markdown-preview-plus-view[data-use-github-style] ol ul {
  margin-top: 0;
  margin-bottom: 0;
}
.markdown-preview-plus-view[data-use-github-style] li > p {
  margin-top: 16px;
}
.markdown-preview-plus-view[data-use-github-style] dl {
  padding: 0;
}
.markdown-preview-plus-view[data-use-github-style] dl dt {
  padding: 0;
  margin-top: 16px;
  font-size: 1em;
  font-style: italic;
  font-weight: bold;
}
.markdown-preview-plus-view[data-use-github-style] dl dd {
  padding: 0 16px;
  margin-bottom: 16px;
}
.markdown-preview-plus-view[data-use-github-style] blockquote {
  padding: 0 15px;
  color: #777;
  border-left: 4px solid #ddd;
}
.markdown-preview-plus-view[data-use-github-style] blockquote > :first-child {
  margin-top: 0;
}
.markdown-preview-plus-view[data-use-github-style] blockquote > :last-child {
  margin-bottom: 0;
}
.markdown-preview-plus-view[data-use-github-style] table {
  display: block;
  width: 100%;
  overflow: auto;
  word-break: normal;
  word-break: keep-all;
}
.markdown-preview-plus-view[data-use-github-style] table th {
  font-weight: bold;
}
.markdown-preview-plus-view[data-use-github-style] table th,
.markdown-preview-plus-view[data-use-github-style] table td {
  padding: 6px 13px;
  border: 1px solid #ddd;
}
.markdown-preview-plus-view[data-use-github-style] table tr {
  background-color: #fff;
  border-top: 1px solid #ccc;
}
.markdown-preview-plus-view[data-use-github-style] table tr:nth-child(2n) {
  background-color: #f8f8f8;
}
.markdown-preview-plus-view[data-use-github-style] img {
  max-width: 100%;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
.markdown-preview-plus-view[data-use-github-style] .emoji {
  max-width: none;
}
.markdown-preview-plus-view[data-use-github-style] span.frame {
  display: block;
  overflow: hidden;
}
.markdown-preview-plus-view[data-use-github-style] span.frame > span {
  display: block;
  float: left;
  width: auto;
  padding: 7px;
  margin: 13px 0 0;
  overflow: hidden;
  border: 1px solid #ddd;
}
.markdown-preview-plus-view[data-use-github-style] span.frame span img {
  display: block;
  float: left;
}
.markdown-preview-plus-view[data-use-github-style] span.frame span span {
  display: block;
  padding: 5px 0 0;
  clear: both;
  color: #333;
}
.markdown-preview-plus-view[data-use-github-style] span.align-center {
  display: block;
  overflow: hidden;
  clear: both;
}
.markdown-preview-plus-view[data-use-github-style] span.align-center > span {
  display: block;
  margin: 13px auto 0;
  overflow: hidden;
  text-align: center;
}
.markdown-preview-plus-view[data-use-github-style] span.align-center span img {
  margin: 0 auto;
  text-align: center;
}
.markdown-preview-plus-view[data-use-github-style] span.align-right {
  display: block;
  overflow: hidden;
  clear: both;
}
.markdown-preview-plus-view[data-use-github-style] span.align-right > span {
  display: block;
  margin: 13px 0 0;
  overflow: hidden;
  text-align: right;
}
.markdown-preview-plus-view[data-use-github-style] span.align-right span img {
  margin: 0;
  text-align: right;
}
.markdown-preview-plus-view[data-use-github-style] span.float-left {
  display: block;
  float: left;
  margin-right: 13px;
  overflow: hidden;
}
.markdown-preview-plus-view[data-use-github-style] span.float-left span {
  margin: 13px 0 0;
}
.markdown-preview-plus-view[data-use-github-style] span.float-right {
  display: block;
  float: right;
  margin-left: 13px;
  overflow: hidden;
}
.markdown-preview-plus-view[data-use-github-style] span.float-right > span {
  display: block;
  margin: 13px auto 0;
  overflow: hidden;
  text-align: right;
}
.markdown-preview-plus-view[data-use-github-style] code,
.markdown-preview-plus-view[data-use-github-style] tt {
  padding: 0;
  padding-top: 0.2em;
  padding-bottom: 0.2em;
  margin: 0;
  font-size: 85%;
  background-color: rgba(0, 0, 0, 0.04);
  border-radius: 3px;
}
.markdown-preview-plus-view[data-use-github-style] code:before,
.markdown-preview-plus-view[data-use-github-style] tt:before,
.markdown-preview-plus-view[data-use-github-style] code:after,
.markdown-preview-plus-view[data-use-github-style] tt:after {
  letter-spacing: -0.2em;
  content: "\00a0";
}
.markdown-preview-plus-view[data-use-github-style] code br,
.markdown-preview-plus-view[data-use-github-style] tt br {
  display: none;
}
.markdown-preview-plus-view[data-use-github-style] del code {
  text-decoration: inherit;
}
.markdown-preview-plus-view[data-use-github-style] pre > code {
  padding: 0;
  margin: 0;
  font-size: 100%;
  word-break: normal;
  white-space: pre;
  background: transparent;
  border: 0;
}
.markdown-preview-plus-view[data-use-github-style] .highlight {
  margin-bottom: 16px;
}
.markdown-preview-plus-view[data-use-github-style] .highlight pre,
.markdown-preview-plus-view[data-use-github-style] pre {
  padding: 16px;
  overflow: auto;
  font-size: 85%;
  line-height: 1.45;
  background-color: #f7f7f7;
  border-radius: 3px;
}
.markdown-preview-plus-view[data-use-github-style] .highlight pre {
  margin-bottom: 0;
  word-break: normal;
}
.markdown-preview-plus-view[data-use-github-style] pre {
  word-wrap: normal;
}
.markdown-preview-plus-view[data-use-github-style] pre code,
.markdown-preview-plus-view[data-use-github-style] pre tt {
  display: inline;
  max-width: initial;
  padding: 0;
  margin: 0;
  overflow: initial;
  line-height: inherit;
  word-wrap: normal;
  background-color: transparent;
  border: 0;
}
.markdown-preview-plus-view[data-use-github-style] pre code:before,
.markdown-preview-plus-view[data-use-github-style] pre tt:before,
.markdown-preview-plus-view[data-use-github-style] pre code:after,
.markdown-preview-plus-view[data-use-github-style] pre tt:after {
  content: normal;
}
.markdown-preview-plus-view[data-use-github-style] kbd {
  display: inline-block;
  padding: 3px 5px;
  font-size: 11px;
  line-height: 10px;
  color: #555;
  vertical-align: middle;
  background-color: #fcfcfc;
  border: solid 1px #ccc;
  border-bottom-color: #bbb;
  border-radius: 3px;
  box-shadow: inset 0 -1px 0 #bbb;
}
.markdown-preview-plus-view[data-use-github-style] span.critic.comment > span {
  background-color: #fff;
}
.markdown-preview-plus-view[data-use-github-style] a {
  color: #337ab7;
}
.markdown-preview-plus-view[data-use-github-style] pre,
.markdown-preview-plus-view[data-use-github-style] code {
  color: inherit;
}
.markdown-preview-plus-view[data-use-github-style] pre,
.markdown-preview-plus-view[data-use-github-style] pre.editor-colors {
  padding: 0.8em 1em;
  margin-bottom: 1em;
  font-size: 0.85em;
  border-radius: 4px;
  overflow: auto;
}

.bracket-matcher .region {
  border-bottom: 1px dotted lime;
  position: absolute;
}
.line-number.bracket-matcher.bracket-matcher {
  color: #555;
  background-color: rgba(255, 255, 134, 0.34);
}

.spell-check-misspelling .region {
  border-bottom: 2px dotted rgba(255, 51, 51, 0.75);
}
.spell-check-corrections {
  width: 25em !important;
}

pre.editor-colors {
  background-color: white;
  color: #555;
}
pre.editor-colors .invisible-character {
  color: rgba(85, 85, 85, 0.2);
}
pre.editor-colors .indent-guide {
  color: rgba(85, 85, 85, 0.2);
}
pre.editor-colors .wrap-guide {
  background-color: rgba(85, 85, 85, 0.2);
}
pre.editor-colors .gutter {
  color: #555;
  background: white;
}
pre.editor-colors .gutter .line-number.folded,
pre.editor-colors .gutter .line-number:after,
pre.editor-colors .fold-marker:after {
  color: #e87b00;
}
pre.editor-colors .invisible {
  color: #555;
}
pre.editor-colors .selection .region {
  background-color: #e1e1e1;
}
pre.editor-colors .bracket-matcher .region {
  background-color: #C9C9C9;
  opacity: .7;
  border-bottom: 0 none;
}
pre.editor-colors.is-focused .cursor {
  border-color: black;
}
pre.editor-colors.is-focused .selection .region {
  background-color: #afc4da;
}
pre.editor-colors.is-focused .line-number.cursor-line-no-selection,
pre.editor-colors.is-focused .line.cursor-line {
  background-color: rgba(255, 255, 134, 0.34);
}
pre.editor-colors .syntax--source.syntax--gfm {
  color: #444;
}
pre.editor-colors .syntax--gfm .syntax--markup.syntax--heading {
  color: #111;
}
pre.editor-colors .syntax--gfm .syntax--link {
  color: #888;
}
pre.editor-colors .syntax--gfm .syntax--variable.syntax--list {
  color: #888;
}
pre.editor-colors .syntax--markdown .syntax--paragraph {
  color: #444;
}
pre.editor-colors .syntax--markdown .syntax--heading {
  color: #111;
}
pre.editor-colors .syntax--markdown .syntax--link {
  color: #888;
}
pre.editor-colors .syntax--markdown .syntax--link .syntax--string {
  color: #888;
}
.syntax--comment {
  color: #999988;
  font-style: italic;
}
.syntax--string {
  color: #D14;
}
.syntax--string .syntax--source,
.syntax--string .syntax--meta.syntax--embedded.syntax--line {
  color: #5A5A5A;
}
.syntax--string .syntax--punctuation.syntax--section.syntax--embedded {
  color: #920B2D;
}
.syntax--string .syntax--punctuation.syntax--section.syntax--embedded .syntax--source {
  color: #920B2D;
}
.syntax--constant.syntax--numeric {
  color: #D14;
}
.syntax--constant.syntax--language {
  color: #606aa1;
}
.syntax--constant.syntax--character,
.syntax--constant.syntax--other {
  color: #606aa1;
}
.syntax--constant.syntax--symbol {
  color: #990073;
}
.syntax--constant.syntax--numeric.syntax--line-number.syntax--find-in-files .syntax--match {
  color: rgba(143, 190, 0, 0.63);
}
.syntax--variable {
  color: #008080;
}
.syntax--variable.syntax--parameter {
  color: #606aa1;
}
.syntax--keyword {
  color: #222;
  font-weight: bold;
}
.syntax--keyword.syntax--unit {
  color: #445588;
}
.syntax--keyword.syntax--special-method {
  color: #0086B3;
}
.syntax--storage {
  color: #222;
}
.syntax--storage.syntax--type {
  color: #222;
}
.syntax--entity.syntax--name.syntax--class {
  text-decoration: underline;
  color: #606aa1;
}
.syntax--entity.syntax--other.syntax--inherited-class {
  text-decoration: underline;
  color: #606aa1;
}
.syntax--entity.syntax--name.syntax--function {
  color: #900;
}
.syntax--entity.syntax--name.syntax--tag {
  color: #008080;
}
.syntax--entity.syntax--other.syntax--attribute-name {
  color: #458;
  font-weight: bold;
}
.syntax--entity.syntax--name.syntax--filename.syntax--find-in-files {
  color: #E6DB74;
}
.syntax--support.syntax--constant,
.syntax--support.syntax--function,
.syntax--support.syntax--type {
  color: #458;
}
.syntax--support.syntax--class {
  color: #008080;
}
.syntax--invalid {
  color: #F8F8F0;
  background-color: #00A8C6;
}
.syntax--invalid.syntax--deprecated {
  color: #F8F8F0;
  background-color: #8FBE00;
}
.syntax--meta.syntax--structure.syntax--dictionary.syntax--json > .syntax--string.syntax--quoted.syntax--double.syntax--json,
.syntax--meta.syntax--structure.syntax--dictionary.syntax--json > .syntax--string.syntax--quoted.syntax--double.syntax--json .syntax--punctuation.syntax--string {
  color: #000080;
}
.syntax--meta.syntax--structure.syntax--dictionary.syntax--value.syntax--json > .syntax--string.syntax--quoted.syntax--double.syntax--json {
  color: #d14;
}
.syntax--meta.syntax--diff,
.syntax--meta.syntax--diff.syntax--header {
  color: #75715E;
}
.syntax--css.syntax--support.syntax--property-name {
  font-weight: bold;
  color: #333;
}
.syntax--css.syntax--constant {
  color: #099;
}
</style>

  </head>
  <body class="markdown-preview-plus-view">
    <h2>Dynamic Programming</h2>
<p>Dynamic Programming (DP) is a method for solving a complex problem by breaking
it down into a collection of simpler subproblems, solving each of those
subproblems just once, and storing their solutions for later looking up instead
of recomputation.
DP has two key attributes : optimal substructure and overlapping
sub-problems. If a problem can be solved by combining optimal solutions
to non-overlapping sub-problems, the strategy is called
“divide and conquer” instead.</p>
<h3>Steps</h3>
<ul>
<li>Find recursive variable $dp$
Setup border condition
$$dp[i] = init$$</li>
<li>Find recursive rules
$$dp[i] = f([dp[j]]_{j=0…i-1})$$</li>
<li>Iteration and apply rules
<ul>
<li>Top-down</li>
<li>Bottom-up</li>
</ul>
</li>
</ul>
<h3>Two approaches:</h3>
<ul>
<li>
<p><strong>Top-down approach</strong>   We define a solution table. We look up the table
for solutions,  if not recorded we compute and save the its solution to the table.
compute it otherwise.</p>
</li>
<li>
<p><strong>Bottom-up approach</strong> We solve the  first and use their solutions to build-on
and arrive at solutions to bigger sub-problems.</p>
</li>
</ul>
<h3>Typical problems</h3>
<p>The DP problem can be summarized into the following types.</p>
<h4>1. k depth recursion</h4>
<p>In this type problems, the DP rule is simple. $dp[i]$ can be expressed as
a simple function of k number of previous solutions. The time complexity is $O(n)$
for 1D and $O(mn)$ for 2D. The space complexity is the same, but can be further
reduced to $O(1)$, since we just need k previous solutions. We could use $dp1,dp2,…dpk$
to replace $dp[0…n-1]$.</p>
<p>$$dp[i] = f(dp[i-1], dp[i-1],…,dp[i-k])$$
For example in 62.Unique Paths, the dp variable is Fibonacci numbers, and
rule is $dp[i]=dp[i-1]+dp[i-2]$ .</p>
<p><strong>1D</strong></p>
<p>70.<a href="http://oj.leetcode.com/problems/climbing-stairs/">Climbing Stairs</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int climbStairs(int n) {</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;int&gt; dp={1,2};</span></span></span>
<span class="syntax--text syntax--plain"><span> </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=2;i&lt;n;i++)dp.push_back(dp[i-2]+dp[i-1]);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span> return dp[n-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>91.<a href="https://leetcode.com/problems/decode-ways">Decode Ways</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int numDecodings(string s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>  </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n = s.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>  if(!n || s[0] == '0')</span></span></span>
<span class="syntax--text syntax--plain"><span>      </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span>  </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int f[n+1] = {1, 1};</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>  for( int i = 2; i &lt;= n; ++i)</span></span></span>
<span class="syntax--text syntax--plain"><span>       </span><span class="syntax--meta syntax--paragraph syntax--text"><span>f[i] = (s[i-1] != '0')*f[i-1] + ((s[i-2] == '1') || (s[i-2] == '2' &amp;&amp; s[i-1] &lt;= '6'))*f[i-2];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>return f[n];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<ol start="639">
<li><a href="https://leetcode.com/problems/decode-ways-ii">Decode Ways II</a></li>
</ol>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int numDecodings(string s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>long e0 = 1, e1 = 0, e2 = 0, f0 = 0, M = 1e9 + 7;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for (char c : s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if (c == '*') {</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>f0 = 9 * e0 + 9 * e1 + 6 * e2;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>            e1 = e0;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>            e2 = e0;</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>} else {</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>f0 = (c &gt; '0') * e0 + e1 + (c &lt;= '6') * e2;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>            e1 = (c == '1') * e0;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>            e2 = (c == '2') * e0;</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        e0 = f0 % M;</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    return e0;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>198.<a href="https://leetcode.com/problems/house-robber/">House Robber</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int rob(vector&lt;int&gt;&amp; nums) {</span></span></span>
<span class="syntax--text syntax--plain"><span>   </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(nums.empty())return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n = nums.size();</span></span></span>
<span class="syntax--text syntax--plain"><span>     </span><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;int&gt; dp={0,nums[0]};</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=2;i&lt;=n;++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp.push_back(max(dp[i-1], nums[i-1]+dp[i-2]));</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return dp[n];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>213.<a href="https://leetcode.com/problems/house-robber-ii/">House Robber II</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int rob(vector&lt;int&gt;&amp; nums) {</span></span></span>
<span class="syntax--text syntax--plain"><span>   </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(nums.empty())return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n = nums.size();</span></span></span>
<span class="syntax--text syntax--plain"><span>     </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(n==1) return nums[0];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;int&gt; dp1={0,nums[0]}, dp2={nums[n-1],nums[n-1]};</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for(int i=2;i&lt; n;++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp1.push_back(max(dp1[i-1], nums[i-1]+dp1[i-2]));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        dp2.push_back(max(dp2[i-1], nums[i-1]+dp2[i-2]));</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return max( dp1[n-1], dp2[n-2]);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p><strong>2D</strong>
62. <a href="https://leetcode.com/problems/unique-paths">Unique Paths</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int uniquePaths(int m, int n) {</span></span></span>
<span class="syntax--text syntax--plain"><span> </span><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;vector&lt;int&gt;&gt;path(m, vector&lt;int&gt;(n,1));</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span> </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=1;i&lt;m;++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>     </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=1;j&lt;n;++j){</span></span></span>
<span class="syntax--text syntax--plain"><span>         </span><span class="syntax--meta syntax--paragraph syntax--text"><span>path[i][j]=path[i-1][j]+path[i][j-1];</span></span></span>
<span class="syntax--text syntax--plain"><span>     </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span> </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span> return path[m-1][n-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span> }</span></span></span>
</pre>
<p>63.<a href="https://leetcode.com/problems/unique-paths-ii">Unique Paths II</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int uniquePathsWithObstacles(vector&lt;vector&lt;int&gt;&gt;&amp; grid) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int m=grid.size(), n=grid[0].size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    vector&lt;vector&lt;int&gt;&gt;path(m, vector&lt;int&gt;(n,0));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    if(grid[m-1][n-1]==1) return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span>     </span><span class="syntax--meta syntax--paragraph syntax--text"><span>path[m-1][n-1]=1;</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>  </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=m-2;i&gt;=0;i--){</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>path[i][n-1]=grid[i][n-1]==1? 0:  path[i+1][n-1];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for(int j=n-2;j&gt;=0;j--){</span></span></span>
<span class="syntax--text syntax--plain"><span>          </span><span class="syntax--meta syntax--paragraph syntax--text"><span>path[m-1][j]=grid[m-1][j]==1? 0:  path[m-1][j+1];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>   </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=m-2;i&gt;=0;--i){</span></span></span>
<span class="syntax--text syntax--plain"><span>      </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=n-2;j&gt;=0;--j){</span></span></span>
<span class="syntax--text syntax--plain"><span>          </span><span class="syntax--meta syntax--paragraph syntax--text"><span>path[i][j]= grid[i][j]==1? 0:  path[i+1][j]+path[i][j+1];</span></span></span>
<span class="syntax--text syntax--plain"><span>      </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>  </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>return path[0][0];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<ol start="64">
<li><a href="https://leetcode.com/problems/minimum-path-sum">Minimum Path Sum</a></li>
</ol>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int minPathSum(vector&lt;vector&lt;int&gt;&gt;&amp; grid) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int m=grid.size(), n= grid[0].size();</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=m-2;i&gt;=0;--i ) grid[i][n-1]= grid[i][n-1] + grid[i+1][n-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for(int j=n-2;j&gt;=0;--j ) grid[m-1][j]= grid[m-1][j] + grid[m-1][j+1];</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=m-2;i&gt;=0;--i){</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=n-2;j&gt;=0;--j){</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>grid[i][j]=grid[i][j]+min(grid[i+1][j],grid[i][j+1]);</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    return grid[0][0];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<h4>3. Whole path recursion</h4>
<p>In this type problems, $dp[i]$ is defined as a function of all previous soltion.
a simple function of k number of previous solutions. The time complexity is $O(n^2)$
for 1D. The space complexity is $O(n)$.</p>
<ol start="95">
<li><a href="https://leetcode.com/problems/unique-binary-search-trees">Unique Binary Search Trees</a></li>
</ol>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int numTrees(int n) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;int&gt;dp(n+1,0);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    dp[0]=1;</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=1;i&lt;n+1;++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=0;j&lt;i;++j)</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i]+=dp[j]*dp[i-j-1];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>   </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return dp[n];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>647.<a href="https://leetcode.com/problems/palindromic-substrings">Palindromic Substrings</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int countSubstrings(string s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n =s.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    vector&lt;int&gt;dp(n+1,0);</span></span></span>
<span class="syntax--text syntax--plain"><span>     </span><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;vector&lt;bool&gt;&gt; m(n, vector&lt;bool&gt;(n, false));</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i = n-1; i&gt;=0; --i){</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i]+=dp[i+1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int j = i; j&lt;n;++j){</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(i==j || (s[i]==s[j]&amp;&amp; (m[i+1][j-1]||j==i+1))){</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>m[i][j]=true;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                dp[i]+= 1;</span></span></span>
<span class="syntax--text syntax--plain"><span>             </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    return dp[0];</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p><a href="https://leetcode.com/problems/palindrome-partitioning-ii">132. Palindrome Partitioning II</a>
Two dp variable dp and m are running here.</p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int minCut(string s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n=s.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    vector&lt;int&gt; dp;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for(int i=0; i&lt;=n; ++i) dp.push_back(n-i-1);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    vector&lt;vector&lt;bool&gt;&gt; m(n, vector&lt;bool&gt;(n, false));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for(int i = n-1; i&gt;=0; --i){</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j = i; j&lt;n;++j){</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(i==j || (s[i]==s[j]&amp;&amp; (m[i+1][j-1]||j==i+1))){</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>m[i][j]=true;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                dp[i]=min(dp[i], 1+dp[j+1]);</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    return dp[0];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>Iterate by length of substrings.
516. <a href="https://leetcode.com/problems/longest-palindromic-subsequence">Longest Palindromic Subsequence</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int longestPalindromeSubseq(string s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n =s.size(), ans=0;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    vector&lt;vector&lt;int&gt;&gt;dp(n,vector&lt;int&gt;(n,0));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for(int i=0; i&lt;n; ++i) dp[i][i]=1;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for(int len = 2; len &lt;= n; ++len){ //traverse the length</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i = 0; i &lt;= n - len; ++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int j = i + len -1;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>            if(s[i]==s[j]) dp[i][j]=dp[i+1][j-1]+2;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>            else dp[i][j]= max(dp[i+1][j], dp[i][j-1]);</span></span></span>
<span class="syntax--text syntax--plain"><span>         </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>       </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return dp[0][n-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p><a href="https://leetcode.com/problems/count-different-palindromic-subsequences">730. Count Different Palindromic Subsequences</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int countPalindromicSubsequences(const string&amp; s) {</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>static constexpr long mod = 1000000007;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    int n = s.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    vector&lt;vector&lt;int&gt;&gt; dp(n, vector&lt;int&gt;(n, 0));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for (int i = 0; i &lt; n; ++i) dp[i][i] = 1;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for (int len = 1; len &lt;= n; ++len) {</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for (int i = 0; i &lt; n - len; ++i) {</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>const int j = i + len;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>            if (s[i] == s[j]) {</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i][j] = dp[i + 1][j - 1] * 2;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                int l = i + 1, r = j - 1;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                while (l &lt;= r &amp;&amp; s[l] != s[i]) ++l;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                while (l &lt;= r &amp;&amp; s[r] != s[i]) --r;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                if (l == r) dp[i][j] += 1;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                else if (l &gt; r) dp[i][j] += 2;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                else dp[i][j] -= dp[l + 1][r - 1];</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>} else {</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i][j] = dp[i][j - 1] + dp[i + 1][j] - dp[i + 1][j - 1];</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i][j] = (dp[i][j] + mod) % mod;</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    return dp[0][n - 1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<h4>4. Global local maximization</h4>
<p>The type of problem involves two dp. One is to
find local maximum by n-depth or whole path recursion. The other is
find the global maximum from local maximum.</p>
<p><a href="https://leetcode.com/problems/maximum-subarray/">53.Maximum Subarray</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int maxSubArray(vector&lt;int&gt;&amp; nums) {</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int sum= 0, ans= INT_MIN;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for (auto x:nums){</span></span></span>
<span class="syntax--text syntax--plain"><span>         </span><span class="syntax--meta syntax--paragraph syntax--text"><span>sum = max(sum+x, x);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>         ans = max(sum, ans);</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    return ans;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>152.<a href="https://leetcode.com/problems/maximum-product-subarray/">Maximum Product Subarray</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int maxProduct(vector&lt;int&gt;&amp; nums) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(nums.empty()) return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    int ans, curMax, curMin;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    ans = curMax = curMin = nums[0];</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=1;i&lt;nums.size();++i) {</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int x=nums[i];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        if(x&lt;0) swap(curMin, curMax);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        curMax = max(x, x*curMax);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        curMin = min(x, x*curMin);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        ans = max(ans, curMax);</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    return ans;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>300.<a href="https://leetcode.com/problems/longest-increasing-subsequence/">Longest Increasing Subsequence</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int lengthOfLIS(vector&lt;int&gt;&amp; nums) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(nums.empty()) return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    int n = nums.size();</span></span></span>
<span class="syntax--text syntax--plain"><span>   </span><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;int&gt; dp(n,1);</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=1;i&lt;n;++i)</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=0;j&lt;i;++j)</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(nums[i]&gt;nums[j])</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i]=max(dp[i],dp[j]+1);</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return *max_element(dp.begin(),dp.end());</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>Using push new element to the back of the answer array if increasing or replace
the lower_bound.</p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int lengthOfLIS(vector&lt;int&gt;&amp; nums) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;int&gt; dp;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for (int x : nums) {</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>auto ix = lower_bound (dp.begin(), dp.end(), x);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        if (ix == dp.end()) dp.push_back(x);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        else *ix = x;</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    return dp.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>368.<a href="https://leetcode.com/problems/largest-divisible-subset/">Largest Divisible Subset</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;int&gt; largestDivisibleSubset(vector&lt;int&gt;&amp; nums) {</span></span></span>
<span class="syntax--text syntax--plain"><span>   </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n = nums.size(), left=0, len=0;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>   vector&lt;int&gt; dp(n,0),pre(n, 0), ans;</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>sort(nums.begin(), nums.end());</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for(int i=n-1;i&gt;=0; --i)</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=i;j&lt; n;++j)</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(nums[j]%nums[i]==0 &amp;&amp; dp[j]+1&gt;dp[i]){</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i] = dp[j]+1,pre[i] = j;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                if(dp[i] &gt; len) len = dp[i], left=i;            }</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>   </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=0; i&lt; len; ++i) ans.push_back(nums[left]), left=pre[left];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return ans;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>32.<a href="https://leetcode.com/problems/longest-valid-parentheses/">Longest Valid Parentheses</a></p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int longestValidParentheses(string s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n =s.size(), ans =0;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    vector&lt;int&gt; dp(n+1,0);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for (int i = 2; i &lt;= n; i++) {</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if (s[i-1] == ')') {</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if (s[i-2] == '(') dp[i] = dp[i-2] +2;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                else {</span></span></span>
<span class="syntax--text syntax--plain"><span>                    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int start =i-2-dp[i-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                    if (s[start] == '(')  dp[i] = dp[i-1] + 2 + dp[start];</span></span></span>
<span class="syntax--text syntax--plain"><span>              </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        ans = max(ans,dp[i]);</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return ans;</span></span></span>
<span class="syntax--text syntax--plain"><span>  </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<p>Alternate solution: using stack</p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int longestValidParentheses(string s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>stack&lt;int&gt; stk;   // positions first: index, second: 0:'(', 1:')'</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    int maxLen = 0, last=-1;</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int i=0; i&lt;s.size(); i++) {</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(s[i]=='(') stk.push(i);   // left parenthesis</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        else if (s[i] == ')') {          // right parenthesis</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(stk.empty()) last=i;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>            else {</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>stk.pop();</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int cnt = stk.empty()? i-last: i-stk.top();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                maxLen = max(maxLen, cnt);</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<h4>5. Between two Subsequences</h4>
<p>This type of problem usually involves Transformation a string s1 to another s2.
The $dp[i][j]$ is defined as a function of subsequence $s1[0…i-1]$ and
$s2[0…i-1]$. The update of $dp[i][j]$ depends on comparison between $s1[i-1]$
and  $s2[i-1]$. $dp$ is a 2-D array. The time complexity is $O(n^2)$ and the
space complexity is $O(n^2)$.</p>
<ol start="712">
<li><a href="https://leetcode.com/problems/minimum-ascii-delete-sum-for-two-strings">Minimum ASCII Delete Sum for Two Strings</a></li>
</ol>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int minimumDeleteSum(string s1, string s2) {</span></span></span>
<span class="syntax--text syntax--plain"><span>          </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n1 = s1.size(), n2 = s2.size();</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;vector&lt;int&gt;&gt; dp(n1+1, vector&lt;int&gt;(n2+1,0));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n1;++i) dp[i][0] = s1[i-1]+dp[i-1][0];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n2;++i) dp[0][i] = s2[i-1]+dp[0][i-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n1; ++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=1; j&lt;=n2; ++j){</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(s1[i-1]==s2[j-1]) dp[i][j] = dp[i-1][j-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                else dp[i][j]=  min(dp[i][j-1 ]+s2[j-1],dp[i - 1][j]+s1[i-1]);</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        return dp[n1][n2];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<ol start="583">
<li><a href="https://leetcode.com/problems/delete-operation-for-two-strings">Delete Operation for Two Strings</a></li>
</ol>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int minDistance(string s1, string s2) {</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n1 = s1.size(), n2 = s2.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        vector&lt;vector&lt;int&gt;&gt; dp(n1+1, vector&lt;int&gt;(n2+1,0));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n1;++i) dp[i][0] = i;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n2;++i) dp[0][i] = i;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n1; ++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=1; j&lt;=n2; ++j){</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(s1[i-1]==s2[j-1]) dp[i][j] = dp[i-1][j-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                else dp[i][j]=  min(dp[i][j-1 ],dp[i - 1][j])+1;</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        return dp[n1][n2];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<ol start="72">
<li><a href="https://leetcode.com/problems/edit-distance/">Edit Distance</a></li>
</ol>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int minDistance(string word1, string word2) {</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n1 = word1.size(), n2 = word2.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        vector&lt;vector&lt;int&gt;&gt; dp(n1+1, vector&lt;int&gt;(n2+1,0));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=0; i&lt;=n1;++i) dp[i][0] = i;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=0; i&lt;=n2;++i) dp[0][i] = i;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n1; ++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=1; j&lt;=n2; ++j){</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(word1[i-1]==word2[j-1]) dp[i][j] = dp[i-1][j-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                else dp[i][j]=  min(dp[i - 1][j - 1], min(dp[i - 1][j], dp[i][j - 1])) + 1;</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        return dp[n1][n2];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<ol start="115">
<li><a href="https://leetcode.com/problems/distinct-subsequences">Distinct Subsequences</a></li>
</ol>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int numDistinct(string s2, string s1) {</span></span></span>
<span class="syntax--text syntax--plain"><span>         </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n1 = s1.size(), n2 = s2.size();</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>vector&lt;vector&lt;int&gt;&gt; dp(n1+1, vector&lt;int&gt;(n2+1,0));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=0; i&lt;=n2;++i) dp[0][i] = 1;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n1; ++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=1; j&lt;=n2; ++j){</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(s1[i-1]==s2[j-1]) dp[i][j] =dp[i][j-1 ]+dp[i - 1][j - 1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>                else dp[i][j]= dp[i][j - 1];</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        return dp[n1][n2];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<ol start="97">
<li><a href="https://leetcode.com/problems/interleaving-string/">Interleaving String</a></li>
</ol>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span>   </span><span class="syntax--meta syntax--paragraph syntax--text"><span>bool isInterleave(string s1, string s2, string s3) {</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n1 = s1.size(), n2 = s2.size(), n3 = s3.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        if(n3 != n1+n2) return false;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        vector&lt;vector&lt;bool&gt;&gt; dp(n1+1, vector&lt;bool&gt;(n2+1,true));</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n1;++i) dp[i][0] = dp[i-1][0]&amp;&amp;s1[i-1]==s3[i-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n2;++i) dp[0][i] = dp[0][i-1]&amp;&amp;s2[i-1]==s3[i-1];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for(int i=1; i&lt;=n1; ++i){</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for(int j=1; j&lt;=n2; ++j){</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i][j]= dp[i-1][j]&amp;&amp;s1[i-1] == s3[i+j-1] ||dp[i][j-1]&amp;&amp;s2[j-1] == s3[i+j-1];</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        return dp[n1][n2];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>

<h4>6. Break the subsequence</h4>
<p>This type of problem usually involves collect rewards for some action at the
element of  sequence, which will reduce the sequence. The target is to maximizing
the rewards. The $dp[i][j]$ is defined on a subsequence from ith to jth. We need
another iteration from i to j to find the local minimal. The time complexity is
$O(n^3)$.</p>
<ol start="312">
<li><a href="">Burst Balloons</a></li>
</ol>
<p>$$dp[i][j] = \max_{k=i…j}([dp[i][k-1]+ dp[k+1][j]+f[k])$$</p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int maxCoins(vector&lt;int&gt;&amp; nums) {</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>     </span><span class="syntax--meta syntax--paragraph syntax--text"><span>nums.insert(nums.begin(), 1), nums.push_back(1);   // add 1 at both first and last for convenience</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n = nums.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    vector&lt;vector&lt;int&gt;&gt; dp(n, vector&lt;int&gt;(n,0));// dp[l][r] is the max result of nums[l - r] inclusively</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    for (int j = 1; j &lt; n-1; j++)</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for (int i = j; i &gt; 0; i--)</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>for (int k = i; k &lt;= j; k++)            // treat k as the last balloons bursted</span></span></span>
<span class="syntax--text syntax--plain"><span>                </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i][j] = max(dp[i][j], dp[i][k - 1] + nums[i - 1] * nums[k] * nums[j + 1] + dp[k + 1][j]);</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return dp[1][n - 2];</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<ol start="546">
<li><a href="https://leetcode.com/problems/remove-boxes">Remove Boxes</a></li>
</ol>
<p>Top down solution</p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int removeBoxes(vector&lt;int&gt;&amp; s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>   </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(s.empty()) return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int dp[100][100][100] = {0};</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    function&lt;int(int, int , int)&gt; dfs =[&amp;](int i, int j, int k){</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if (i &gt; j) return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        if (dp[i][j][k]) return dp[i][j][k];</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        while(j&gt;i&amp;&amp;s[j]==s[j-1]) j--,k++;</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i][j][k] = dfs(i, j - 1, 0) + (1 + k) * (1 + k);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for (int pos = i; pos &lt; j; pos++) {</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if (s[pos] == s[j]) dp[i][j][k] = max(dp[i][j][k], dfs(i, pos, k+1) + dfs(pos + 1, j - 1, 0));</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        return dp[i][j][k];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>};</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    return dfs(0, s.size()-1, 0);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>
<ol start="664">
<li><a href="https://leetcode.com/problems/strange-printer">Strange Printer</a></li>
</ol>
<p>Topdown solution</p>
<pre class="editor-colors lang-text"><span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>int strangePrinter(string s) {</span></span></span>
<span class="syntax--text syntax--plain"><span>     </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if(s.empty()) return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>int n = s.size();</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>    vector&lt;vector&lt;int&gt;&gt; dp(n, vector&lt;int&gt;(n,0));</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>function&lt;int(int, int)&gt; dfs =[&amp;](int i, int j){</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if (i &gt; j) return 0;</span></span></span>
<span class="syntax--text syntax--plain"><span>         </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if (dp[i][j]) return dp[i][j];</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>dp[i][j] = dfs(i, j - 1)+1;</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        for (int pos = i; pos &lt; j; pos++) {</span></span></span>
<span class="syntax--text syntax--plain"><span>            </span><span class="syntax--meta syntax--paragraph syntax--text"><span>if (s[pos] == s[j]) dp[i][j]= min(dp[i][j], dfs(i, pos) + dfs(pos+1, j-1));</span></span></span>
<span class="syntax--text syntax--plain"><span>        </span><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>        return dp[i][j];</span></span></span>
<span class="syntax--text syntax--plain"><span>    </span><span class="syntax--meta syntax--paragraph syntax--text"><span>};</span></span></span>
<span class="syntax--text syntax--plain"><span></span></span>
<span class="syntax--text syntax--plain"><span>  </span><span class="syntax--meta syntax--paragraph syntax--text"><span>return dfs(0, n-1);</span></span></span>
<span class="syntax--text syntax--plain"><span class="syntax--meta syntax--paragraph syntax--text"><span>}</span></span></span>
</pre>

  </body>
</html>
