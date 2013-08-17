scan-fs
=======

Scans the file system in nodejs

在nodejs环境下扫描文件系统的工具。
例子：
-----

var scanFS = require('scan-fs' ).create();
//scanFS.exclude(__filename);
//scanFS.exclude(/dir.*/);
scanFS.exclude('*dir*');
/*scanFS.exclude(['*index.js']);
 scanFS.exclude(/.*index.js$/);
 scanFS.exclude(new RegExp(/.*index.js$/));*/

scanFS.listeners({
	'file': function(filePath, eOpts){
		console.log('File: ' + filePath);
	},
	'directory': function(path, eOpts){
		console.log('Directory: ' + path);
	},
	'error': function(err){
		console.log('err:' , err);
	},
	'complete': function(fileCount, dirCount){
		console.log('complete: ' + fileCount + ' files, ' + dirCount + ' directory')
	},
	'root': function(path, eventArgs){
		console.log('root: ' + path);
	},
	'path': function(path, eOpts){
		console.log('path: ' + path);
	}
	}).setRecursive(true).scan('/home/lg/workspace/nodejs');
