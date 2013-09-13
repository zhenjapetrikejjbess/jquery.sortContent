/**
 *jQuery Plugin SortContent
 *
 * https://github.com/abdennour/jquery.sortContent
 * @author Abdennour TOUMI<abdennour.toumi@estifeda.com>
 * @requires JQuery
 * @param options {Object} override default values
 * @constructor
 */
/*!
 * jQuery Plugin SortContent
 * Copyright (c) 2013-2014 Abdennour TOUMI <abdennour.toumi@estifeda.com>
 * The MIT License
 *
 * Permission is hereby granted, free of charge, to any person obtaining a copy
 * of this software and associated documentation files (the "Software"), to deal
 * in the Software without restriction, including without limitation the rights
 * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
 * copies of the Software, and to permit persons to whom the Software is
 * furnished to do so, subject to the following conditions:
 *
 * The above copyright notice and this permission notice shall be included in
 * all copies or substantial portions of the Software.
 *
 * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
 * THE SOFTWARE.
 */
 
 (function($) {
    var methdSorContent={
			targetFn:function($this){
				return methdSorContent.realSelected($this);
			},
			init:function(args,$th){
				var defau={
						asc:true,
						helper:function($child){
							return $child.html();
						},
						target:function($child,index){
							return $child;
						},format:function(html){
							return html.toLowerCase();
						}
				}
				/**
				 * target : 'this','parent',
				 */
				return $.extend({}, defau, args);
			},sortHtmlArray:function(arry,$th,args){
				
				return arry.sort(function(a, b){
			    	 var nameA=args.format(a.html.replace(/(<([^>]+)>)/ig, "")), nameB=args.format(b.html.replace(/(<([^>]+)>)/ig, ""))
			    	 
			    	 if (nameA < nameB) //sort string ascending
			    	  return -1 
			    	 if (nameA > nameB)
			    	  return 1
			    	 return 0 //default return value (no sorting)
			    	});
			},setHTML:function(arryHTML,jqparent,args){
				//console.log(arryHTML);
				methdSorContent.realSelected(jqparent).each(function(i,e){
					args['target']($(e),i).html(arryHTML[i].thtml);
			     });
				return jqparent;
			},getHtml:function(jqparent,args){
				var tmp=[];
				methdSorContent.realSelected(jqparent).each(function(i,e){
			    	 tmp.push({e:$(e),html:args.helper($(e)),thtml:args['target']($(e),i).html()});
			     });
				//console.log(tmp);
				return tmp;
			},realSelected:function(jq){
				if(jq.length<=1){
					return jq.children();
				}else{
					return jq;
				}
			}
	};
	$.fn.sortContent=function(args){
		var tmp;
		args=methdSorContent.init(args,$(this));
	     tmp=methdSorContent.sortHtmlArray(methdSorContent.getHtml($(this),args),$(this),args);
	     if(!args['asc']){
	    	 tmp.reverse();
	     }
	     
	    return methdSorContent.setHTML(tmp, $(this),args);
	     
	};
 
 })(jQuery);
